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

|Switch                |Parameter                          |
|----------------|-------------------------------|
|Mask          |`resource mask - Type,Name,Language <br> commas are mandatory but each of Type, Name & Language are optional`|
|Log          |`Filename or CONSOLE or NUL CONSOLE can be abbreviated to CON Logs the details of the operation performed If this switch is omitted, the log will be written to resourcehacker.log`|
|Script          |`filename - contains a multi-command script, NOT a resource script for more info: -help script`|
|Help          |`options - command-line or script (always logged to CONSOLE) other switches are ignored.`|

# Notes:
- Switch identifiers (except -script) may be abbreviated down to a single char (eg -res or -r).
- Switch instructions do not have to be in any particular order.
- File names that contain spaces must be enclosed within double quotes.

# Batch file Examples
> **(using rh.exe instead of ResourceHacker.exe in places for brevity)**
- reshack_help.bat:
<code>
ResourceHacker.exe -help
@pause  :: to see the console output before the CMD window closes.
  </code>
  
-reshack_compile_res_script.bat:
<code>
rh.exe -open .\in\resources.rc -save .\out\resources.res -action compile -log NUL
</code>

-reshack_add_icon_to_old.bat:
<code>
rh.exe -open old.exe -save new.exe -action addskip -res my.ico -mask ICONGROUP,MAINICON,
</code>

-reshack_extract_all_source_icons_to_icons_folder.bat:
<code>
rh.exe -open source.exe -save .\icons -action extract -mask ICONGROUP,, -log CON
@pause
</code>

-reshack_extract_all_dialogs.bat:
<code>
rh.exe -open source.exe -save .\dialogs.rc -action extract -mask DIALOG,, -log rh.log
</code>

-reshack_execute_my_script.bat:
<code>
ResourceHacker.exe -script myscript.txt
</code>

# Resource Hacker™ Scripts:
- Resource Hacker™ Scripts are executed from the command-line using the following syntax:
<code>
ResourceHacker.exe -script ScriptFile
</code>

- Resource Hacker™ Scripts are text files with the following format:
<code>
//comments are preceded by double slashes
  [FILENAMES]
  Open=
  Save=
  Log=
  [COMMANDS]
  //one or more of the following commands ...
  -add          SourceFile, ResourceMask
  -addskip      SourceFile, ResourceMask
  -addoverwrite SourceFile, ResourceMask
  -addoverwrite SourceFile, ResourceMask
  -modify       SourceFile, ResourceMask
  -extract      TargetFile or TargetFolder, ResourceMask
  -delete       ResourceMask
  -changelanguage(langID)
</code>

# Note: Filenames that include spaces must be enclosed within double quotes.
## Resource Hacker™ Script examples:
- rh_script_myprog_rus.txt
<code>
//This script deletes all Language Neutral (0)
  //string-table, menu and dialog resource items
  //in MyProg.exe before replacing them
  //with Russian (1049) items...	
  [FILENAMES]
  Exe=    MyProg.exe
  SaveAs= MyProg_Rus.exe
  Log=    MyProg_Rus.log	
  [COMMANDS]
  -delete  MENU,,0
  -delete  DIALOG,,0
  -delete  STRINGTABLE,,0
  -add     MyProg_Rus.res, MENU,,1049
  -add     MyProg_Rus.res, DIALOG,,1049
  -add     MyProg_Rus.res, STRINGTABLE,,1049
</code>

- rh_script_myprog_upd_images.txt
<code>
//This script updates 2 bitmaps and an
  //icon in MyProg.exe ...	
  [FILENAMES]
  Exe=    MyProg.exe
  SaveAs= MyProg_Updated.exe	
  [COMMANDS]
  -addoverwrite Bitmap128.bmp, BITMAP,128,
  -addoverwrite Bitmap129.bmp, BITMAP,129,0
  -addoverwrite MainIcon.ico, ICONGROUP,MAINICON,0
</code>

- rh_script_myprog_upd_all.txt
<code>
//This script replaces all resources
  //in MyProg.exe with all the resources
  //in MyProgNew.res	
  [FILENAMES]
  Exe=    MyProg.exe
  SaveAs= MyProg_Updated.exe
  [COMMANDS]
  -delete  ,,,            //delete all resources before...
  -add MyProgNew.res ,,,  //adding all the new resources
</code>
</code>

# "Packed" or "Compressed" Executables:
### Some executable files are "packed" or "compressed" using compression algorithms. Not only does this reduces file size, it also makes viewing and modifying resources marginally more difficult. I suspect that this resource 'hiding' is (or was) a common objective in this process. Anyhow, in deference to these authors, I've chosen not to unpack files with Resource Hacker. As a side note, it seems that "packed" executables have become quite uncommon over the last 5-10 years, and software authors are exposing more rather than less information in executable resources. I suspect that earlier concerns about the loss of intellectual property with reverse engineering have been allayed.

# Licence to Use - Terms and Conditions:
### This Resource HackerTM software is released as freeware provided that you agree to the following terms and conditions:
- This software is not to be distributed via any website domain or any other media without the prior written approval of the copyright owner.
- This software is not to be used in any way to illegally modify software.

# DISCLAIMER:
### A user of this Resource HackerTM software acknowledges that he or she is receiving this software on an "as is" basis and the user is not relying on the accuracy or functionality of the software for any purpose. The user further acknowledges that any use of this software will be at the user's own risk and the copyright owner accepts no responsibility whatsoever arising from the use or application of the software.

### The above licence terms constitute "copyright management information" within the meaning of Section 1202 of Title 17 of the United States Code and must not be altered or removed from the licensed works. Their alteration or removal from the licensed works, and the distribution of licensed works without all the above licence terms in an unaltered way, may contravene Section 1202 and give rise civil and/or criminal consequences.

# Download version 5.1.7: (Official Download) http://www.angusj.com/resourcehacker/#download
**EXE install (2.9 MB)** [http://www.angusj.com/resourcehacker/reshacker_setup.exe](http://www.angusj.com/resourcehacker/reshacker_setup.exe)

**ZIP install (3.0 MB)** [http://www.angusj.com/resourcehacker/resource_hacker.zip](http://www.angusj.com/resourcehacker/resource_hacker.zip)

# Download version (Alternative Download Link) 5.1.7:
**SETUP EXE İnstall (2.9 MB)** [https://github.com/EkeLachin/ResourceHacker/raw/main/Setup%C4%B0nstall.exe](https://github.com/EkeLachin/ResourceHacker/raw/main/Setup%C4%B0nstall.exe)


**ZİP İnstall (3.0 MB)** [https://github.com/EkeLachin/ResourceHacker/archive/refs/heads/main.zip](https://github.com/EkeLachin/ResourceHacker/archive/refs/heads/main.zip)
# Changes in 5.1.7:
- Bugfix: fixed broken Accelerator compiling
