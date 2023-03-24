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

A complete list of Resource-Definition Statements can be found [here.](https://msdn.microsoft.com/en-us/library/windows/desktop/aa381043(v=vs.85).aspx)

Additional features of Resource Hacker's compiler include: The #INCLUDE directive (to access definition statements in header files etc) can be nested to multiple levels, as can the #IF, and #IFDEF directives. #DEFINE, #UNDEF, #IF, #ELIF, #ELSE, #IFDEF, #IFNDEF, #INCLUDE, and #PRAGMA directives are all supported. Strings, between double-quote (") characters, may contain typical 'C' style backslashed 'escaped' characters — \t , \n , \\ , \" , \x, \u and \377 (octal). A double-quote within a string must be 'escaped' using either a preceding backslash or with another double-quote. Script comments are preceded either by double forward-slashes (//) or by a semi-colon (;). Filenames with relative paths are allowed. Filenames that contain spaces must be enclosed within double-quote characters.

Compiler error messages are reported, even errors nested within INCLUDE statements ...
<img src="https://raw.githubusercontent.com/EkeLachin/ResourceHackerimg/main/resim_2023-03-24_122758432.png">

# Viewing and Editing Resources:
Once a resource file has been opened, its resources will generally be displayed as either an image (or group of images) or as decompiled text. Binary resources, usually images, can't be edited directly with Resource Hacker, but they can still be very easily exported and imported once they've been modified by an external image editor. (I see no benefit in duplicating what third-party image editors do so well.)
<img src="https://raw.githubusercontent.com/EkeLachin/ResourceHackerimg/main/resim_2023-03-24_123140337.png">

<img src="https://raw.githubusercontent.com/EkeLachin/ResourceHackerimg/main/resim_2023-03-24_123357657.png">

# Menu and Dialog resource types have their own WYSIWYG designers:
<img src="https://raw.githubusercontent.com/EkeLachin/ResourceHackerimg/main/resim_2023-03-24_123658372.png">
<img src="https://raw.githubusercontent.com/EkeLachin/ResourceHackerimg/main/resim_2023-03-24_123946881.png">

# Binary resources that have unknown formats will be displayed as read-only binary text. (Any resource can also be viewed in this fashion if desired.)
<img src="https://raw.githubusercontent.com/EkeLachin/ResourceHackerimg/main/resim_2023-03-24_124136287.png">

# Other Actions:
<img src="https://raw.githubusercontent.com/EkeLachin/ResourceHackerimg/main/resim_2023-03-24_124300283.png">

# Command Line Syntax:
Just about all the functionality of Resource Hacker™ can be accessed from the command line without having to open the Resource Hacker™ GUI.
Command line instructions and Resource Hacker™ scripts can remove the drudgery entailed with repeating Resource Hacker™ tasks.
Command-line instructions are a combination of switch statements followed by switch parameters as explained in the following table: **Command line statements:**
|Switch                |Parameter                          |
|----------------|-------------------------------|
|Open|`'filename - the name of the file that is to be modified. It should be a Windows PE file (*.exe, *.dll etc) or a compiled or uncompiled resouce file (*.res or *.rc)'`            |
|Save          |`usually a filename for the new or modified file, but can also be a folder when extracting multiple resources`            |
|Resource          |`filename - contains a resource being added to the opened file.`|
|Action          |`	action to be performed on the opened file`|
- **Add** add a resource, but fails if it already exists
- **Addoverwrite** add a resource, and overwriting if it already exists
- **Addskip** add a resource, but skipping if it already exists
- **Compile** compiles a resource script file (*.rc) to a binary resource file (*.res)
- **Delete-** delete a resource
- **Extract** extract a resource
- **Modify** modify a resource
- **changelanguage(langID)** changes the language of ALL resources
- **Mask** resource mask Type,Name,Language commas are mandatory but each of Type, Name & Language are optional
- **Log** Filename or **CONSOLE** or **NUL**
CONSOLE can be abbreviated to **CON**
Logs the details of the operation performed
If this switch is omitted, the log will be written to *resourcehacker.log*
|Script          |`filename - contains a multi-command script, NOT a resource script for more info: -help script`|
|Help          |`options - command-line or script (always logged to CONSOLE) other switches are ignored.`|

# Notes:
hlelp
