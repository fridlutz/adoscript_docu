---
layout: commandcall
category: CommandCall
title: "FILE_DELETE"
tags: 1.3 1.5
---

FILE_DELETE deletes a file.

# Syntax:  

```adoscript
{% raw %}
CC "AdoScript" FILE_DELETE file:strValue

# --> RESULT ecode:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`file`|strValue, specifies the file to be deleted|

# Returns:  

|`ecode`|intValue, has the value 0 if no errors occured, 1 if the file was not deleted.|

# Remarks:

Relative paths relate to the current working directory (CWD).

Files stored in the ADOxx database can be deleted by preceding the filename with ths string 'db:\'

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "AdoScript" FILE_DIALOG open 
   filter1:"HTML Files" type1:"**.htm" default-ext:"htm" 
	
CC "AdoScript" FILE_DELETE file:(path) 
IF (ecode = 0) {
   CC "AdoScript" INFOBOX ("Deleted the file " + path)
}

{% endraw %}
```
{: .line-numbers}

Lets the user select a file and deletes it.  
