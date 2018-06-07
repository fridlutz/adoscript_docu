---
layout: commandcall
category: CommandCall
title: "FILE_COPY"
tags: 1.3 1.5
---

FILE_COPY copies a file.

# Syntax:  

```adoscript
{% raw %}
CC "AdoSript" FILE_COPY from:strValue to:strValue [ copy-file-attributes ]

# --> RESULT ecode:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`from`|strValue, specifies the source file|
|`to`|strValue, specifies the target file|
|`copy-file-attributes`|modifier|

# Returns:  

|`ecode`|intValue, has the value 0 if no errors occured, 1 if the file was not copied.|

# Remarks:

Relative paths relate to the current working directory (CWD).

Files stored in the ADOxx database can be copied by preceding the filename with ths string 'db:\'

If copy-file-attributes is specified, additionally the file attributes of the source file are copied/set to the target file. E.g. if the source file is write-protected, so will be the target file. This will only work if none of the files are ADOxx database files!

The destination file can only be created if the full filename (drive letter + absolute path + file name) is not longer than 260 characters.

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "AdoScript" FILE_DIALOG open 
   filter1:"HTML Files" type1:"**.htm" default-ext:"htm" 
	
CC "AdoScript"  GET_TEMP_FILENAME

CC "AdoScript" FILE_COPY from:(path) to:(filename)
IF (ecode = 0) {
   CC "AdoScript" INFOBOX ("Copied the file " + path + " to " + filename)
}

{% endraw %}
```
{: .line-numbers}

Lets the user select a file and copies it to the temp directory.  
