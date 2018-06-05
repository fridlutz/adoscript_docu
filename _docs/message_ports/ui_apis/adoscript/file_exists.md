---
layout: commandcall
category: CommandCall
title: "FILE_EXISTS"
tags: 1.3 1.5
---

FILE_EXISTS checks if the sepcified files exists. It works with both DB files and file system files.

# Syntax:  

```adoscript
{% raw %}
CC "AdoScript" FILE_EXISTS file:strValue

# -->RESULT exists: 1|0
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`file`|strValue, the name of the file to be checked|

# Returns:  

|`exists`|1|0, is set to 1 (true) if the file exists and to 0 (false) otherwise.|

# Remarks:

Relative paths relate to the current working directory (CWD).  
If you check for DB files, you have to prefix the string with "db:\\".  
FILE_EXISTS checks only for files which are attached to the current application library!

# See Also:  



Example 1:

```adoscript
{% raw %}

# check if the file version.txt exists in the CWD
CC "AdoScript" FILE_EXISTS file:"version.txt"
IF (exists) {
    CC "AdoScript" INFOBOX "File exists!"
} ELSE {
    CC "AdoScript" INFOBOX "File does not exist!"
}
# check if the DB file reginald.ini exists
CC "AdoScript" FILE_EXISTS file:"db:\\reginald.ini"
IF (exists) {
    CC "AdoScript" INFOBOX "DB-File exists!"
} ELSE {
    CC "AdoScript" INFOBOX "DB-File does not exist!"
}

{% endraw %}
```
{: .line-numbers}

