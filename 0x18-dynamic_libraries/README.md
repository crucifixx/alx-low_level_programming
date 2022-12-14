C DYNAMIC/SHARED LIBRARIES
Requirements

    Language: C
    OS: Ubuntu 14.04 LTS
    Compiler: gcc 4.8.4
    Style guidelines: [Betty style] (https://github.com/holbertonschool/Betty/wiki)

Synopsis

This repository illustrates how to create a dynamic library in Linux. To read how to do so, read my blog here
Description of important files:

    create_dynamic_lib.sh - shell script to create dynamic library named liball.so
    libholberton.so - created this dynamic library containing some functions as liball.so
    functions_folder - all .c files hold functions; all .o files were used to create dynamic library
    holberton.h - included function prototypes of functions in library
    len - executable program to run 0-main.c
    100-operations.so - created this C dynamic library to be imported into python program 100-tests.py

