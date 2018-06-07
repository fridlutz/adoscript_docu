---
layout: commandcall
category: CommandCall
title: "DIR_REMOVE"
tags: 1.3 1.5
---

DIR_REMOVE removes a directory.

# Syntax:  

```adoscript
{% raw %}
CC "AdoScript" DIR_REMOVE path:strValue.

#--> RESULT ecode:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`path`|strValue, the path to the directory to be removed|

# Returns:  

|`ecode`|intValue|

# Remarks:

Relative paths relate to the current working directory (CWD). The directory can only be removed if it is empty.  

The return variable ecode has the value 0 if no errors occured, a value different than 0 if an error occured.

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "AdoScript" DIR_CREATE path:("c:\\temp\\testdir")
IF (ecode = 0) {
  CC "AdoScript" DIR_REMOVE path:("c:\\temp\\testdir")
  IF (ecode = 0) {
    CC "AdoScript" INFOBOX ("Directory successful removed.")
  }
  ELSE {
    CC "AdoScript" INFOBOX ("Directory could not be removed.")
  }
}
ELSE {
  CC "AdoScript" INFOBOX ("Directory already exists or cannot be created.")
}
{% endraw %}
```
{: .line-numbers}
Crates a new directory and removes it afterwards.

