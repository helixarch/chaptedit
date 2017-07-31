chaptedit
=========

Command-line ogm (txt) type chapters editor written in BASH.

Can read xml type as well, but the output is always txt.
- - - - -

### FEATURES
>- Basic clean-up
>- Shift time
>- Convert fps
>- Adjust time
>- Synchronize chapters files
>- Search text
>- Replace text
>- Join chapters files
>- Split chapters files

>     Also:
>- Supports wildcards
>- Supports absolute and relative paths
>- Process all chapters files inside a directory
>- Use multiple parameters in the same command and they'll run one after the other
>- Works on Linux, Cygwin and Bash shell on Windows 10 as well
>- Comprehensive help with over 40 examples
- - - - -

### SCREENSHOTS
![Help examples](https://camo.githubusercontent.com/5bff9f48eec8017d27b6a93eeff4d97ba81daaf6/687474703a2f2f3134312e3233372e302e33363a35303030312f6368617074656469745f68656c705f6578616d706c65732e706e67)  
Help examples

<br>

![Wildcard support](https://camo.githubusercontent.com/e6efd3a47fb8595a0edd1c2111b9aed2f35df784/687474703a2f2f3134312e3233372e302e33363a35303030312f6368617074656469745f77696c64636172642e706e67)  
Wildcard support
- - - - -

### PARAMETERS OVERVIEW
    -i    Chapters file to process.  
    -d    Directory containing chapters files to process.  
    -r    Recurse. Optional. Use with -d.  
    -b    Backup input file. Optional. Use with any other parameter.  
    -s    Shift time.  
    -p    Convert fps. NTSC to PAL.  
    -n    Convert fps. PAL to NTSC.  
    -a    Adjust time.  
    -1    Adjust time.  
    -2    Adjust time.  
    -y    Synchronize with file.  
    -D    Synchronize with directory. Use with -d.  
    -Y    Synchronize chapter times one by one. Optional. Use with -y or -D.  
    -f    Search, case insensitive.  
    -F    Search, case sensitive. 
    -e    Replace, case insensitive.  
    -E    Replace, case sensitive.  
    -j    Join two chapters files.  
    -J    Join time. Optional. Use with -j.  
    -x    Split chapters file.  
    -X    Split time. Optional. Use with -x.  
    -h    Help.  
    -H    Help with more information and examples.
- - - - -

### PARAMETERS
`-i "Input file"`
>Chapters file to process.  
Accepts ogm (txt) or xml files.  
Supports wildcards and relative or absolute paths.  
Open a chapters file with no other parameters to perform basic clean-up (empty chapters are removed etc).  
Does not work with -D parameter (synchronize with directory) and -r parameter (recurse).

<br>

`-d "Input directory"`
>Directory containing chapters files to process.  
Can contain ogm (txt), xml or both types.  
Supports wildcards and relative or absolute paths.  
Open a directory with no other parameters to perform basic clean-up to all contained chapters files.  
Works with all parameters except with -y (synchronize with file) and -j (join two chapters files).  
Instead of Synchronize with file you can use Synchronize with directory (-D parameter).

<br>

`-r [Switch]`
>Recurse.  
Optional switch, to be used with -d.  
>Searches recursively for chapters files.

<br>

`-b [Switch]`
>Backup input file.  
Optional switch that can be used with any other parameter.  
Makes a copy of the input file in the same directory with the .bak suffix.  
If the backup already exists, it does nothing. If -b is not set and the backup file exists, it is removed.

<br>

`-s (+/-/a/z)hh:mm:ss,fff`
>Shift time.  
Plus sign (or no sign at all) adds time, where the minus sign subtracts time.  
"a" and "z" indicate absolute time value for the beginning and end time of the chapters file respectively.  
In this case the shifting time will be calculated.

<br>

`-p [Switch]`
>Convert fps.  
Change the fps from NTSC (23.976/29.970) to PAL (25).

<br>

`-n [Switch]`
>Convert fps.  
Change the fps from PAL (25) to NTSC (23.976/29.970).

<br>

`-a (+/-)hh:mm:ss,fff (+/-)hh:mm:ss,fff`
>Adjust time.  
Beginning and end time will be set to these values and the rest will be adjusted proportionally.  
The time value is absolute if you don't use the +/- and will be shifted if you do use either sign.

<br>

`-1 (+/-)hh:mm:ss,fff`
>Adjust time.  
Beginning time will be set to this value and the rest will be adjusted proportionally.  
The time value is absolute if you don't use the +/- and will be shifted if you do use either sign.

<br>

`-2 (+/-)hh:mm:ss,fff`
>Adjust time.  
End time will be set to this value and the rest will be adjusted proportionally.  
The time value is absolute if you don't use the +/- and will be shifted if you do use either sign.

<br>

`-y "Input file"`
>Synchronize with file.  
Supports relative or absolute paths.  
The chapter times of the file given with -i parameter will be adjusted with beginning and end time of this file.

<br>

`-D "Input directory"`
>Synchronize with directory.  
To be used only with -d parameter.  
This directory contains chapters files with correct times.  
Supports relative or absolute paths.  
The two directories (given with -d and -D parameters) must contain chapters files with the same names.  
Synchronizes each chapters file in the input directory (-d) with the chapters file with the same name  
that's in the directory (-D).

<br>

`-Y [Switch]`
>Synchronize chapter times one by one.  
Optional switch to be used with -y and -D.  
Replaces times of file to be synchronized with times of synchronization file, respectively.

<br>

`-f "Find text"`
>Search, case insensitive.  
The double quotes are necessary.

<br>

`-F "Find text"`
>Search, case sensitive.  
The double quotes are necessary.

<br>

`-e "Text to be replaced" "New text"`
>Replace, case insensitive.  
The double quotes are necessary.

<br>

`-E "Text to be replaced" "New text"`
>Replace, case sensitive.  
The double quotes are necessary.

<br>

`-j "Input file"`
>Join two chapters files.  
Supports relative or absolute paths.  
This file will be appended to the file given with -i parameter.

<br>

`-J hh:mm:ss,fff`
>Join time.  
Optional parameter, to be used with -j.  
Shifts the time after beginning of the second file in the output file.

<br>

`-x (+/-)hh:mm:ss,fff` *`or`* `(+/-)SUB_INTEGER` *`or`* `(+/-)INTEGER:INTEGERt` *`or`* `(+/-)INTEGER:INTEGERn`
>Split chapters file.  
Can take 4 different syntaxes:  
>1. `(+/-)hh:mm:ss,fff:` splitting time.
>2. `(+/-)SUB_INTEGER:` splitting chapter integer.
>3. `(+/-)INTEGER:INTEGERt:` fraction where we split the chapters file according to total time.
>4. `(+/-)INTEGER:INTEGERn:` fraction where we split the chapters file according to number of chapters.  

>The minus sign means that counting begins from the end of the chapters file.  
The plus sign means that counting begins from the beginning. (Equivalent of using no sign at all).

<br>

`-X [Switch]`
>Split time.  
Optional switch, to be used with -x.  
Makes the second generated txt begin with time 00:00:00,000.  
Can be used with any -x syntax.

<br>

`-h [Switch]`
>Display help.

<br>

`-H [Switch]`
>Display help with more information and examples.
