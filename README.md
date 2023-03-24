# ResourceHacker
A freeware resource compiler &amp; decompiler for Windows® applications. http://www.angusj.com/resourcehacker/
- Version 5.1.7
- Last updated: 3 January 2019
- Copyright © 1999-2019 Angus Johnson
- Freeware - no nags, no ads and fully functional.
- [Download](https://github.com/EkeLachin/ResourceHacker/archive/refs/heads/main.zip)
# Overview
Resource Hacker™ is a resource editor for 32bit and 64bit Windows® applications. It's both a **resource compiler** (for .rc files), and a **decompiler** - enabling viewing and editing of resources in executables (*.exe; *.dll; *.scr; etc) and compiled resource libraries (*.res, *.mui). While Resource Hacker™ is primarily a GUI application, it also provides many options for compiling and decompiling resources from the command-line.

<img src="https://raw.githubusercontent.com/EkeLachin/ResourceHackerimg/main/resim_2023-03-24_121304145.png">

<img src="https://raw.githubusercontent.com/EkeLachin/ResourceHackerimg/main/resim_2023-03-24_121947871.png">

# Compiling:
Compiling can be initiated either by opening an existing resource script file, or by creating one from scratch using Resource Hacker's editor.

A complete list of Resource-Definition Statements can be found [here](https://msdn.microsoft.com/en-us/library/windows/desktop/aa381043(v=vs.85).aspx)

Additional features of Resource Hacker's compiler include: The #INCLUDE directive (to access definition statements in header files etc) can be nested to multiple levels, as can the #IF, and #IFDEF directives. #DEFINE, #UNDEF, #IF, #ELIF, #ELSE, #IFDEF, #IFNDEF, #INCLUDE, and #PRAGMA directives are all supported. Strings, between double-quote (") characters, may contain typical 'C' style backslashed 'escaped' characters — \t , \n , \\ , \" , \x, \u and \377 (octal). A double-quote within a string must be 'escaped' using either a preceding backslash or with another double-quote. Script comments are preceded either by double forward-slashes (//) or by a semi-colon (;). Filenames with relative paths are allowed. Filenames that contain spaces must be enclosed within double-quote characters.

Compiler error messages are reported, even errors nested within INCLUDE statements ...
