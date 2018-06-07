---
layout: commandcall
category: CommandCall
title: "DIRECTORY_DIALOG"
tags: 1.3 1.5
---

DIRECTORY_DIALOG opens a system dialog which lets the user choose a directory.

# Syntax:  

```adoscript
{% raw %}
CC "AdoScript" DIRECTORY_DIALOG [path:strValue].

#--> RESULT endbutton:["ok"|"cancel"] path:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`path`|strValue|

# Returns:  

|`endbutton`|strValue, ["ok"|"cancel"]|
|`path`|strValue|

# Remarks:

The user can only selected directories on mapped network drives, because ADOxx does not really supprt stuff like Desktop, Trash can etc.  
You can only select one directory!  
You can set the starting directory by passing the parameter path which should contain the path which should be preselected! path may not contain a trailing backslash ('\') except it is the root directory! (path:"c:\\" or path:"c:\\temp" are valid but path:"c:\\temp\\" is not!)

endbutton is set to "ok" if the user pressed the OK button and to "cancel" if the user cancelled the dialog.  
path contains the full selected path if the user pressed OK!

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "AdoScript" DIRECTORY_DIALOG
IF (endbutton = "ok")
{
   CC "AdoScript" INFOBOX (path)
}

{% endraw %}
```
{: .line-numbers}

