---
layout: commandcall
category: CommandCall
title: "DIR_LIST"
tags: 1.3 1.5
---

DIR_LIST returns a list of files and dirs in a directory.

# Syntax:

```adoscript
{% raw %}
CC "AdoScript" DIR_LIST path:strValue [ filemask:strValue ] .

#--> RESULT ecode:intValue files:strValue dirs:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`path`|strValue, the directory to be listed|
|`filemask`|strValue, specifies a format like "**.htm". If no filemask is specified '**' would be taken.|

# Returns:  

|`ecode`|intValue|
|`files`|strValue|
|`dirs`|strValue|

# Remarks:

Relative paths relate to the current working directory (CWD).

All files and dirs are seperated with a '**' because files may contain spaces.

The return variable ecode has the value 0 if no errors occured, a value different than 0 if an error occured.

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "AdoScript" DIR_LIST path:("c:\\")
IF (ecode != 0)
{
  CC "AdoScript" INFOBOX ("Directory doesnt exist or an error occured.")
  EXIT
}
SET myFiles:(replall(files,"**","\n"))
SET myDirs:(replall(dirs,"**","\n"))
CC "AdoScript" INFOBOX ("All files:\n\n" + myFiles + "\n\nAll dirs:\n\n" + myDirs)

{% endraw %}
```
{: .line-numbers}
Displays all files and subdirs of a directory in a infobox. Each file  and dir in a line.

Example 2:

```adoscript
{% raw %}

CC "AdoScript" DIR_LIST path:("C:\\WINNT\\Help") filemask:("**.htm")
IF (ecode != 0)
{
  CC "AdoScript" INFOBOX ("Directory doesnt exist or an error occured.")
  EXIT
}
SET myFiles:(replall(files,"**","\n"))
CC "AdoScript" INFOBOX ("All html-files:\n" + myFiles)

{% endraw %}
```
{: .line-numbers}
Displays all html-files of a directory in a infobox. Each file in a line.

