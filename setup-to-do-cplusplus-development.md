
- [prerequisites](#prerequisites)
- [system setup](#system-setup)
  - [install c/c++ compiler](#install-cc-compiler)
  - [install python](#install-python)
  - [install c/c++ package manager](#install-cc-package-manager)
  - [vscode setup](#vscode-setup)
    - [isntall extensions](#isntall-extensions)
    - [Open the project folder](#open-the-project-folder)
    - [Select a Kit (Compiler)](#select-a-kit-compiler)
    - [Build and run the project](#build-and-run-the-project)
    - [simplest init a cmake project](#simplest-init-a-cmake-project)
- [vcpkg as package manager](#vcpkg-as-package-manager)
    - [vcpkg usual operations](#vcpkg-usual-operations)
    - [vcpkg common problems](#vcpkg-common-problems)

## prepare

for machine learning, c/c++ and python languages are popular in some cases. below we will be introduced how to prepare c/c++ env and multi python versions env. the introduction is mainly focus on windows platform, the macos and linux will be partly introduced at the same time.

# prerequisites

At first, you will need to install Git, CMake and Visual Studio Code.

- GIT, [Git Version control system](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
- CMake, [CMake is used as a building tool for the project on both Windows and Linux](https://cmake.org/install/).cmake related knowleage is very big,  [awesome-cmake](https://github.com/onqtam/awesome-cmake) maybe a suitable entry for guys.   
- Visual Studio Code,[Visual Studio Code (VS Code) is a code editor](https://code.visualstudio.com/download).

in windows, use [scoop](https://scoop.sh/) as the installer to install them is very easy. `scoop install cmake git vscode` 

in macos, `$ xcode-select --install ` is going to install various command line utilities like g++, clang, git, make etc. However it does not install cmake. suggest use brew to install cmake. e.g.

```sh
$ /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
$ brew install cmake
```

# system setup


## install c/c++ compiler

Assuming you have already installed the c/c++ compiler environment.

- windows, `choco install visualstudio2022community` in windows; 
- macos, Clang is available on MacOS by defatul; 
- linux, `apt-get install g++`

## install python

suggest using pyenv(simple python version management tool) to install python.  the pyenv can do switching between multiple versions of Python.

refer [pyenv](https://github.com/pyenv/pyenv) to install it. specially:

- linux, refer [how-to-install-pyenv-python-version-manager-on-ubuntu](https://brain2life.hashnode.dev/how-to-install-pyenv-python-version-manager-on-ubuntu-2004) to install pyenv.;
- macos, consider installing with Homebrew. [Python Development on macOS with pyenv](https://jordanthomasg.medium.com/python-development-on-macos-with-pyenv-2509c694a808) maybe a Detailed guidance.
- windows, you can easy do it through `scoop install pyenv` .  through that way, we will install pyenv-win.

use `pyenv install -l` to list all available python versions, then install the your selection, for example, execute `pyenv install 3.11.0b4 2.7.18` to install  3.11.0b4 python and 2.7.18 python, then execute `pyenv global 3.11.0b4` to set the global python version to be 3.11.0b4.



## install c/c++ package manager

althrough the c/C++ language specification does not require packages nor package managers. There is no concept of packages in the c/C++ specification, if need to add dependency of a third-party lib, you can :

- wrapper the third-party lib's head and binary in your source
- compile the third-party source lib with your project
- use tools likes pkg_config, find in cmake, and so on
- use c/c++ package manager like vcpkg and conan
  
the conan and vcpkg is the common c/c++ package manager, But you need to be mentally prepared, they may not be easy to use, they are not same level as the pip of python, the npm of nodejs, cargo of rust and so on.

to manage the c/c++ building process, you can do it by: muanlly, makefile, visual studio ide, xcode, and so on. to cross platform, we suggest to use **cmake**. 

refer [vcpkg getting started](https://vcpkg.io/en/getting-started.html) documents to install vcpkg. specially, if your platform is windows, you can easy do it through `scoop install vcpkg` .

refer [conan.io](https://conan.io/) documents to install conan., if your platform is windows, you can easy do it through `scoop install conan` .

## vscode setup

the setup will be done directly in vscode, the first step is to launch vscode.

### isntall extensions
to install vscode extensionsPress, follow these instructions: firstly (Ctrl + Shift + X) to open the Extensions menu. then search for the given Extension Pack. last hi Install button.

we should install:
- C/C++ Extension
- CMake Extenstion
- CMake Tools Extension

### Open the project folder

Open the course project folder (Ctrl + O). Here select the top most folder. 

Make sure that you have placed the project into a folder with writing permissions, for example, use your home folder. Also, make sure that the path does not contains diacritics and spaces as some platforms do not handle these correctly.
Link the VCPKG toolchain file

when you use VCPKG as the c/c++ package manager, In order to connect the CMakeTools extension together with VCPKG, it is necessary to edit VS Code settings. To do so:

1. Open the Command Palette (Ctrl+Shift+P) and run the Open Settings (JSON) command.

2. Add the cmake.configureSettings entry and set the path of the CMAKE_TOOLCHAIN_FILE to the vcpkg.cmake file located in your VCPKG installation. Here you need the path from the VCPKG installation process mentioned in the section on how to Install VCPKG.
The settings.json file should then look like this (be aware of the slashes orientation):
```json
    {
        "cmake.configureSettings": {
            "CMAKE_TOOLCHAIN_FILE":
                "{vcpk_repository}/scripts/buildsystems/vcpkg.cmake",
        }
    }
```    
Note: The configuration entry might be added to User, Workspace, or Global settings. In case you work with multiple CMake projects on your computer and you want different settings for each project, we recommend setting the configuration entry in your Workspace settings file otherwise it is probably easier to do it on the User level. The User settings are global for your user account.

if using VCPKG, according to building target triplet,  suggest add "VCPKG_TARGET_TRIPLET" configuration like below: 
```json
    {
        "cmake.configureSettings": {
            "VCPKG_TARGET_TRIPLET": "x64-windows"
        }
    }
```    



### Select a Kit (Compiler)

Before you can use the CMake Tools extension to build a project, you need to configure it to know about the compilers on your system. Do that by scanning for 'kits'. A kit represents a toolchain, which is the compiler, linker, and other tools used to build your project. To scan for kits:

- With an open project open the Command Palette (Ctrl+Shift+P) and run **CMake: Select a Kit**. The extension will automatically scan for kits on your computer and create a list of compilers found on your system.
- Select the compiler you want to use. 

above also can be accessed by directly clicking icon on the bootom toolbar, the icon named **click to change the active kit**.

On Windows we recommend the Visual Studio Build Tools 2022 release - amd64. The amd64 version is used to build on 64-bit for 64-bit. The amd64_x86 version is used to build on 64-bit for 32-bit etc.

### Build and run the project
Start by clicking on the triangle icon in the bottom toolbar. When first compiling the project it may take a while. VCPKG needs to install some dependencies first.

Build and Run
Select a launch target from the menu.


### simplest init a cmake project

below demo shows how to simplest create a init cmake project.


```shell
$ mkdir demo
$ cd demo
demo\>$ code .
```

now you are in a empty floder, we will create a new c++ project that using cmake as the building system.

in vscode, through "[Ctrl + Shift + P]" execute "cmake: quick start". cmake extension request you enter the project name. the project type( lib or bin).  after then, you will see  build/debug/run icons at the below side of vscode.

how to update the CMakeLists.txt, for more about CMake, please check CMake Documentation, e.g. [3.21 CMake Documentation](https://cmake.org/cmake/help/v3.21/)

if you think above is too simple, you can use [cmake-init](https://github.com/cginternals/cmake-init) to generate a more complex & stronger cmake init configuration.the cmake-init is template for reliable, cross-platform C++ project setup using CMake. 

cmake-init is a python program, using `pip install cmake-init` to install it.  below is simple usage demo:
```sh
$ cmake-init demo
cmake-init is going to generate a C++ project

Use only characters matching the [0-9a-zA-Z-_] pattern
Project name (demo):
.....
$ cd demo
demo\>$ cmake --preset=dev
demo\>$ cmake --build --preset=dev
demo\>$ cmake --build --preset=dev -t run-exe
demo\>$ ctest --preset=dev

```


# vcpkg as package manager

you can refer [vcpkg introduction](https://italiancpp.github.io/wp-statico/www.italiancpp.org/wp-content/uploads/2020/06/Using-vcpkg-at-work-to-manage-your-C-libraries.pdf) to get overview of vcpkg.

install vcpkg:

- for windows: scoop install vcpkg
- for linux/macos: 
 ```sh
  # step 1: Clone the vcpkg repo
  git clone https://github.com/Microsoft/vcpkg.git

  # Make sure you are in the directory you want the tool installed to before doing this.
  # Step 2: Run the bootstrap script to build vcpkg
  ./vcpkg/bootstrap-vcpkg.sh
 ```

Using vcpkg with CMake, In order to use vcpkg with CMake outside of an IDE, you can use the toolchain file:
`cmake -B [build directory] -S . -DCMAKE_TOOLCHAIN_FILE=[path to vcpkg]/scripts/buildsystems/vcpkg.cmake`

Then build with:`cmake --build [build directory]`. 

Using vcpkg with CMake, In order to use vcpkg with CMake inside of vscode IDE, you can add CMAKE_TOOLCHAIN_FILE definition in the project's settings.json, 
    ```json
        "cmake.configureSettings": {
            "CMAKE_TOOLCHAIN_FILE": "[path to vcpkg]/scripts/buildsystems/vcpkg.cmake",
        },
    ```
notes, above description assuming that you use vscode at the editor, cmake as the building system. and you have installed  c/c++, cmake, cmake-tools extentions in vscode ide。 


### vcpkg usual operations


```shell
# install special package, the package will be stored in $(VCPKG_PATH)/packages
\>$ vcpkg install [packages to install]
# list installed packages that with triplet xxx,
\>$ vcpkg list --triplet x64-window
```

- backup and restore
```shell
#backup lib
$vcpkg export eigen3 --zip
The following packages are already built and will be exported:
    eigen3:x64-linux
Exporting package eigen3:x64-linux...
Creating zip archive...
Zip archive exported at: /home/atmel/tool/vcpkg/vcpkg-export-20201119-213739.zip

To use the exported libraries in CMake projects use:
    -DCMAKE_TOOLCHAIN_FILE=[...]/scripts/buildsystems/vcpkg.cmake
$ 
# import the backuped lib
$vcpkg.exe import vcpkg-export-20201119-213739.zip
```

- itegrate static lib
```sh
# e.g. use VCPKG install libxxx, hope the project link with its static lib

$ vcpkg isntall libxxx:x86-windows-static
$ cmake ..... -G "Visual Studio 17 2022" -T host=x86 -A win32 -DCMAKE_TOOLCHAIN_FILE=.../vcpkg.cmake -DVCPKG_TARGET_TRIPLET=x86-windows-static
```

``

### vcpkg common problems

- Downloading https://raw.githubusercontent.com/boostorg/boost/boost-1.73.0/LICENSE_1_0.txt... Failed. Status: 6;"Couldn't resolve host name"

    Solution: DNS is contaminated. You need to add github real IP addresses to the hosts file
    
```
    140.82.114.3 github.com
    199.232.69.194 github.global.ssl.fastly.net
    199.232.68.133 raw.githubusercontent.com
```

