---
layout: commandcall
category: CommandCall
title: "IS_INCLUDED_IN_ACTIVE_VARIANT"
tags: 1.3 1.5
---

IS_INCLUDED_IN_ACTIVE_VARIANT determines whether or not an object is included in the active variant of its model.

# Syntax:  

```adoscript
{% raw %}
CC "Drawing" IS_INCLUDED_IN_ACTIVE_VARIANT objid:intValue

# --> RESULT isincluded:boolValue ecode:intValue 
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`objid`|intValue, the ID of a modeling object or of a connector.|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`isincluded`|boolValue, is 1 if the object in included in the active variant of the object's model and 0 otherwise.|

# Remarks:

As for all commands of the "Drawing" message port, it is not required here to have a model window opened.

# See Also:  



Example:

