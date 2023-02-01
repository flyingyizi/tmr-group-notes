
as a arduino beginner, currently you only research example projects with single .ino file. in the future, if you are planning on making a larger project and splitting things up, you can take advantage of:

- split your components to public libraries. then use those libraries， like the usage of  other arduino core libraries, e.g.  [arduino SoftwareSerial](https://github.com/arduino/ArduinoCore-avr/blob/master/libraries/SoftwareSerial/src/SoftwareSerial.cpp)

- split your componets to private smaller testable pieces of code

Arduino IDE was make for designers/inventors, not for programmers. details refer to [What is Arduino?](https://www.arduino.cc/en/Guide/Introduction). on other word, Programmers will use a fully-fledged IDE which has many features a programmer needs on a daily basis, such as vscode with [vscode-Arduino Plugin](https://marketplace.visualstudio.com/items?itemName=vsciot-vscode.vscode-arduino), vscode with [platformIO-IDE plugin](https://platformio.org/).

below, I will descript how to split large project into multi smaller pieces in vscode-Arduino, or in platformIO-IDE.

## using vscode-Arduino

vscode-Arduino can be looked as the enhanced native Arduino IDE. below description also applies to the native Arduino IDE.

project test1( directory is  D:\test1) demo to one main sketch: mainsketch.ino, and with two private pieces of code: a and b. the 'a' piece implemented by .ino file, the 'b' piece implemented by .cpp file.

```text
PS D:\test1> tree /F
卷 新加卷 的文件夹 PATH 列表
卷序列号为 2261-FF58
D:.
│  a.ino
│  b.cpp
│  b.hpp
│  mainsketch.ino
│
└─.vscode
        arduino.json
        c_cpp_properties.json
```

a.ino file contents:
```c++
void a_setup()
{
    // do something
}

void a_loop()
{
    // do something
}
```        

b.hpp file contents:
```c++
#ifndef _B_h
#define _B_h

void b_setup();
void b_loop();

#endif /* _B_h */
```

b.cpp file contents:
```c++
void b_setup()
{
    // do something
}

void b_loop()
{
    // do something
}
```        

mainsketch.ino file content:
```c++
#include "b.hpp"

void setup()
{
    a_setup();
    b_setup();
}
void loop()
{
    a_loop();
    b_loop();
}
```

## using platformIO-IDE

above description in section **using vscode-Arduino**, also can be applies to platformIO-IDE.

platformIO-IDE also support orianize code in different directories. usage details pls refer the readme file in project created by platformIO-IDE.