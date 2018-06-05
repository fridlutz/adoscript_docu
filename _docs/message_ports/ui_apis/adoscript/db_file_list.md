---
layout: commandcall
category: CommandCall
title: "DB_FILE_LIST"
tags: 1.3 1.5
---

DB_FILE_LIST returns a list of all DB files in the current application library as a string with '**' as separator (because files may contain spaces).

# Syntax:  

```adoscript
{% raw %}
CC "AdoScript" DB_FILE_LIST .

#--> RESULT ecode:intValue files:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

none

# Returns:  

|`ecode`|intValue, has the value 0 if no error occured, a value different than 0 if an error occured.|
|`files`|strValue, a list of files separated by "**"|

# Remarks:



# See Also:  



Example 1:

```adoscript
{% raw %}

CC "AdoScript" DB_FILE_LIST
IF (ecode != 0)
{
  CC "AdoScript" INFOBOX ("An error occured")
  EXIT
}
SET dbFiles:(replall(files,"**","\n"))
CC "AdoScript" INFOBOX ("All DB-Files:\n" + dbFiles)

{% endraw %}
```
{: .line-numbers}

Displays all DB-files in a infobox. Each file in a line.

