chaptedit
=========

Command-line ogm (txt) type chapters editor written in BASH.

Can read xml type as well but the output is always txt.
- - - - -

### PARAMETERS  
`-i "Input file"`  
>Chapters file to process.  
Does not work with -D parameter (synchronize with directory) and -r parameter (recurse).

`-d "Input directory"`
>Directory containing chapters files to process.  
Works with all parameters except with -y (synchronize with file) and -j (join two chapters files).  
Instead of Synchronize with file you can use Synchronize with directory (-D parameter).

`-r [Switch]`
>Searches recursively for chapters files in directory given with -d parameter.

`-b [Switch]`
>Backup input file. Makes a copy of the input file in the same directory with the .bak sufix.  
If the backup already exists, it does nothing. If -b is not set and the backup file exists, it is removed.  
Can be used with any other parameter.

`-s (+/-/a/z)hh:mm:ss,fff`
>Shift time. Plus sign (or no sign at all) adds time, where the minus sign subtracts time.  
"a" and "z" indicate absolute time value for the beginning and end time of the chapters file respectively.  
In this case the shifting time will be calculated.

`-p [Switch]`
>Change the fps from NTSC (23.976/29.970) to PAL (25).

`-n [Switch]`
>Change the fps from PAL (25) to NTSC (23.976/29.970).

`-a (+/-)hh:mm:ss,fff (+/-)hh:mm:ss,fff`
>Adjust time. Beginning and end time will be set to these values and the rest will be adjusted proportionally.  
The time value is absolute if you don't use the +/- and will be shifted if you do use either sign.

`-1 (+/-)hh:mm:ss,fff`
>Adjust time. Beginning time will be set to this value and the rest will be adjusted proportionally.  
The time value is absolute if you don't use the +/- and will be shifted if you do use either sign.

`-2 (+/-)hh:mm:ss,fff`
>Adjust time. End time will be set to this value and the rest will be adjusted proportionally.  
The time value is absolute if you don't use the +/- and will be shifted if you do use either sign.

`-y "Input file"`
>Synchronize with file. The chapter times of the file given with -i parameter will be adjusted with  
beginning and end time of this file.

`-D "Input directory"`
>Synchronize with directory. To be used only with -d parameter.  
This directory contains chapters files with correct times.  
The two directories (given with -d and -D parameters) must contain chapters files with the same names.  
Synchronizes each chapters file in the input directory (-d) with the chapters file with the same name  
that's in the directory (-D).

`-Y [Switch]`
>Synchronize chapter times one by one. Optional switch to be used with -y and -D.  
Replaces times of file to be synchronized with times of synchronization file, respectively.

`-f "Find text"`
>Search, case insensitive. The double quotes are necessary.

`-F "Find text"`
>Search, case sensitive. The double quotes are necessary.

`-e "Text to be replaced" "New text"`
>Replace, case insensitive. The double quotes are necessary.

`-E "Text to be replaced" "New text"`
>Replace, case sensitive. The double quotes are necessary.

`-j "Input file"`
>Join two chapters files. This file will be appended to the file given with -i parameter.

`-J hh:mm:ss,fff`
>Join time. Optional parameter, to be used with -j.  
Shifts the time after beginning of the second file in the output file.

`-x (+/-)hh:mm:ss,fff` *`or`* `(+/-)SUB_INTEGER` *`or`* `(+/-)INTEGER:INTEGERt` *`or`* `(+/-)INTEGER:INTEGERn`
>Split chapters file. Can take 4 different syntaxes:  
>1. `(+/-)hh:mm:ss,fff:` splitting time.
>2. `(+/-)SUB_INTEGER:` splitting chapter integer.
>3. `(+/-)INTEGER:INTEGERt:` fraction where we split the chapters file according to total time.
>4. `(+/-)INTEGER:INTEGERn:` fraction where we split the chapters file according to number of chapters.  

>The minus sign means that counting begins from the end of the chapters file.  
The plus sign means that counting begins from the beginning. (Equivalent of using no sign at all).

`-X [Switch]`
>Split time. Optional switch, to be used with -x. Makes the second generated txt begin with time 00:00:00,000.  
Can be used with any -x syntax.

`-h [Switch]`
>Display help.

`-H [Switch]`
>Display help with more information and examples.
