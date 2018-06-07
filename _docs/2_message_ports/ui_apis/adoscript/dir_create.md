---
layout: commandcall
category: CommandCall
title: "DIR_CREATE"
tags: 1.3 1.5
---

DIR_CREATE creates a new directory.

# Syntax:  
```adoscript
{% raw %}
CC "AdoScript" DIR_CREATE path:strValue

#--> RESULT ecode:intValue .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`path`|strValue, the path to the directory to be created|

# Returns:  

|`ecode`|intValue|

# Remarks:

Mind the masking of backslashes (\\ has to be written for one backslash).

DIR_CREATE can create only one new directory per call, so only the last component of path can name a new directory. Relative paths relate to the current working directory (CWD).

The return variable ecode has the value 0 if no error occured and a value different than 0 otherwise.

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "AdoScript" DIR_CREATE path:"c:\\temp\\testdir"
IF (ecode = 0) {
    CC "AdoScript" INFOBOX "Directory successful created."
} ELSE {
    CC "AdoScript" INFOBOX "Directory could not be created."
}

{% endraw %}
```
{: .line-numbers}

