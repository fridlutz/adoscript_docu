---
layout: commandcall
category: CommandCall
title: "IS_DIR_EMPTY"
tags: 1.3 1.5
---

IS_DIR_EMPTY determines whether a specified directory is empty or not.

# Syntax:  

```adoscript
{% raw %}
CC "AdoScript" IS_DIR_EMPTY	path:strValue

 # --> RESULT isempty:boolValue ecode:intValue .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`path`|strValue, the directory which shall be tested|

# Returns:  

|`isempty`|boolValue|
|`ecode`|intValue|

# Remarks:

Note that backslashes have to be masked (e.g. "c:\\temp\\gen"). Relative paths relate to the current working directory (CWD).

# See Also:



Example 1:

```adoscript
{% raw %}

SET dir:"c:\\temp\\gen"
CC "AdoScript" IS_DIR_EMPTY path:(dir)
IF (ecode) {
    CC "AdoScript" ERRORBOX (dir + " cannot be accessed.")
} 
ELSIF (isempty) {
    CC "AdoScript" INFOBOX (dir + " is empty.")
} 
ELSE {
    CC "AdoScript" INFOBOX (dir + " is not empty.")
}

{% endraw %}
```
{: .line-numbers}

