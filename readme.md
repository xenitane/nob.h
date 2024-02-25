# nob.h

> A minimal utility and build system for C-projects
> BONUS: cross-platform

This provides you with the interfaces for all the utilities you'll probably need along with an optional implementation of them.

## Getting started

1. get the `nob.h` file from this repository and put it in your source code directory.
2. include it using the `#include "<directory>/nob.h"` directive
3. and you are done

Now you have two options:

-   Use the provided implementation: add `#define NOB_IMPL` before including `nob.h` in your source-code.
-   Write your own implementation in a separate or the same file, whichever is more convenient for your use case.

## Features

-   Dynamic Array: Declare a structure with these 3 fields to create a dynamic array type:

    1. pointer to the type of data you want to store with named `items`
    2. size_t count
    3. size_t capacity

    When making a dynamic array, initialize it with `{0}`.

    _Example_:

    ```c
    typedef struct{
        int *items;
        size_t count;
        size_t capacity;
    } dyn_arr;

    dyn_arr da={0};
    ```

    Now you can use the functions to append to the array(one or many items), get items, free the array, etc.

-   String Builder: `NOB_String_Builder` for dynamic strings
    Similar features as the dynamic arrays and you can you the items field of a string builder as a C-string

-   String View: `NOB_String_View` for string views
    Holds a pointer to the character array and the length of the string
    Use `SV_Fmt` and `SV_Arg(sv)` while printing it.
-   Command: `NOB_Cmd` for shell commands you want to execute via this program
    Append the command line arguments to it's object via `nob_cmd_append` and run it via `nob_cmd_run_sync` or `nob_cmd_run_async`
-   File IO operations: You have functions to read/write files, browse directories, do lookups, etc.
-   Rebuilding and Rerunning: When writing code that will change over time and you don't want to hit compile every-time it happens, just add `GO_REBUILD_YOURSELF` some where in your code, preferable the first line of `main(int argc, char** argv)` along with the arguments you want it to run with, preferably the one that main receives. You can also go ahead and modify the compile command along with your own compilation flag and parameters if you'd like.
