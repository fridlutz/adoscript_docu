---
layout: commandcall
category: CommandCall
title: "INCLUDE_INTO_ACTIVE_VARIANT"
tags: 1.3 1.5
---

INCLUDE_INTO_ACTIVE_VARIANT includes a modeling object or a connector into the active variant of a model.

# Syntax:  

```adoscript
{% raw %}
CC "Drawing" INCLUDE_INTO_ACTIVE_VARIANT modelid:intValue objid:intValue

# --> RESULT ecode:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|intValue, the ID of the model|
|`objid`|intValue, the ID of a modeling object or connector which shall be included into the active variant of the model.|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success|

# Remarks:

As for all commands of the "Drawing" message port, it is not required here to have a model window opened.

# See Also:  



Example:

