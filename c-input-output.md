# overview

When we say Input, it means to feed some data into a program. An input can be given in the form of a file or from the command line. C programming provides a set of built-in functions to read the given input and feed it to the program as per requirement.

When we say Output, it means to display some data on screen, printer, or in any file. C programming provides a set of built-in functions to output the data on the computer screen as well as to save it in text or binary files.

notice: `#include <stdio.h>` is a preprocessor directive. It tells the preprocessor to include the contents of the I/O header (<stdio.h>) before the program is compiled.

## singal character I/O

The getchar() and putchar() Functions

- The `int getchar(void)` function reads the next available character from the screen and returns it as an integer. This function reads only single character at a time. You can use this method in the loop in case you want to read more than one character from the screen.

- The `int putchar(int c)` function puts the passed character on the screen and returns the same character. This function puts only single character at a time. You can use this method in the loop in case you want to display more than one character on the screen. Check the following example −

```c
#include <stdio.h>
int main( ) {

   int c;

   printf( "Enter a value :");
   c = getchar( );

   printf( "\nYou entered: ");
   putchar( c );

   return 0;
}
```

## normal I/O

The scanf() and printf() Functions. notice, if you use microsoft visual studio compile, use `scanf_s`.

- The `int scanf(const char *format, ...)` function reads the input from the standard input stream stdin and scans that input according to the format provided.

- The `int printf(const char *format, ...)` function writes the output to the standard output stream stdout and produces the output according to the format provided.

The format can be a simple constant string, but you can specify `%s, %d, %c, %f, etc.`, to print or read strings, integer, character or float respectively. There are many other formatting options available which can be used based on requirements. Let us now proceed with a simple example to understand the concepts better −

```c
#include <stdio.h>
int main( ) {

   char str[100];
   int i;

   printf( "Enter a value :");
   scanf("%s %d", str, &i);

   printf( "\nYou entered: %s %d ", str, i);

   return 0;
}
```
When the above code is compiled and executed, it waits for you to input some text. When you enter a text and press enter, then program proceeds and reads the input and displays it.

**notice**: it should be noted that scanf() expects input in the same format as you provided %s and %d, which means you have to provide valid inputs like "string integer". If you provide "string string" or "integer integer", then it will be assumed as wrong input. Secondly, while reading a string, scanf() stops reading as soon as it encounters a space, so "this is test" are three strings for scanf().

## handling invalid input

As you write programs, you should always consider how users will misuse your programs. A well-coding program will anticipate how users will misuse it, and either handle those cases gracefully or prevent them from happening in the first place (if possible). A program that handles error cases well is said to be robust.

in below inputing integer sample,  show you some different ways to handle those cases.
```c
#include <stdio.h>
#include <string.h>


/*** handling invalid input
 * Types of invalid text input
We can generally separate input text errors into four types:
 * - Input extraction succeeds but the input is meaningless to the program (e.g. entering ‘k’ as your mathematical operator).
 * - Input extraction succeeds but the user enters additional input (e.g. entering ‘*q hello’ as your mathematical operator).
 * - Input extraction fails (e.g. trying to enter ‘q’ into a numeric input).
 * - Input extraction succeeds but the user overflows a numeric value.
 * 
 */
// flushes the standard input, on other word, clears the input buffer.
// To ignore everything up to and including the next ‘\n’ character,
// for case: Extraction succeeds but with extraneous input
// IT SHOULD BE called after scanf in c, or cin statement in c++
void ignore_line()
{
    // in c++ ,use `std::cin.ignore(std::numeric_limits<std::streamsize>::max(), '\n');`
    // in c, use
    while ((getchar()) != '\n')
        ;
}

#define optional_type(type) \
    struct                  \
    {                       \
        bool present;       \
        type value;         \
    }
typedef optional_type(int) optional_int;

optional_int get_int()
{
    int x = 0;
    // if in c++, use `std::cin >> x;` to got input
    // if in c, use
    int ret = scanf_s("%d", &x); // in this case for valid input it should be 1

    // if in c++, use `if (!std::cin) // has a previous extraction failed?`
    // if in c, use
    if (ret != 1)
    {
        // yep, so let's handle the failure, if in c++, use `std::cin.clear()` to put us back in 'normal' operation mode.
        // if in c, use
        clearerr(stdin);
        //
        ignore_line();
        optional_int a = {false, 0};
        return a;
    }
    else // else our extraction succeeded
    {
        ignore_line();
        optional_int a = {true, x};
        return a;
    }
}

optional_int get_int()
{
    int x = 0;
    // if in c++, use `std::cin >> x;` to got input
    // if in c, use
    int ret = scanf_s("%d", &x); // in this case for valid input it should be 1

    // if in c++, use `if (!std::cin) // has a previous extraction failed?`
    // if in c, use
    if (ret != 1)
    {
        // yep, so let's handle the failure, if in c++, use `std::cin.clear()` to put us back in 'normal' operation mode.
        // if in c, use
        clearerr(stdin);
        //
        ignore_line();
        optional_int a = {false, 0};
        return a;
    }
    else // else our extraction succeeded
    {
        ignore_line();
        optional_int a = {true, x};
        return a;
    }
}


int main()
{
    printf("enter a integer value:");
    optional_int r = get_int();
    // Loop until user enters a valid input

    while (r.present == false)
    {
        printf("Oops, that input is invalid.  Please try again.\n");
        printf("enter a integer value:");
        r = get_int();
    }
    printf("%d\n", r.value);
    return 0;
}
```

