---
layout: commandcall
category: CommandCall
title: "FILE_RENAME"
tags: 1.3 1.5
---

FILE_RENAME renames a file.

# Syntax:  

```adoscript
{% raw %}
CC "AdoScript" FILE_RENAME from:strValue to:strValue

# -->RESULT ecode:intValue .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`from`|strValue, the old name|
|`to`|strValue, the new name|

# Returns:  

|`ecode`|intValue, has the value 0 if no errors occured, 1 if the file was not renamed.|

# Remarks:

Relative paths relate to the current working directory (CWD).

Files stored in the ADOxx database can be renamed by preceding the filename with the string 'db:\'

The new name can only be created if the full filename (drive letter + absolute path + file name) is not longer than 260 characters.

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "AdoScript" FILE_RENAME from:"c:\\temp\\myfile.txt" to:"c:\\temp\\mynewfile.txt"

{% endraw %}
```
{: .line-numbers}

