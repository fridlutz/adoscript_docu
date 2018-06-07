---
layout: commandcall
category: CommandCall
title: "SET_ATTR_ACCESS_MODE"
tags: 1.3 1.5
---

SET_ATTR_ACCESS_MODE sets the access mode (write-protected or not) for attribute values in write-protected models.

# Syntax:  

```adoscript
{% raw %}
CC "Modeling" SET_ATTR_ACCESS_MODE [ modeltype:all | modeltype:strValue |
									modelid:id | objid:id ]
									access-mode:AccessMode .


AccessMode :	"default" | "write-protected" | "full" .


# --> RESULT ecode:intValue  .

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modeltype`|all|
|`modeltype`|strValue|
|`modelid`|id|
|`objid`|id|
|`access-mode`|AccessMode|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|


# Remarks:

By default, (most) attribute values can be edited in write-protected models. (This does not mean that changes on a write-protected model can be saved.)  
The attribute access mode can be changed at three levels: for model types, for models and for objects (modeling objects or connectors).  
The attribute access mode for a certain object is determined as follows:  
If a non-default attribute access mode is defined for that object, this mode is taken.  
Otherwise, if a non-default attribute access mode is defined for the model of that object, this mode is taken.  
Otherwise, if a non-default attribute access mode is defined for the model type of that model, this mode is taken.  
Otherwise the result is "not write-protected".  
With modeltype:all the default attribute access mode can be changed. So, if you generally want to write-protect attribute values in write-protected models, call  
CC "Modeling" SET_ATTR_ACCESS_MODE  
modeltype:all access-mode:"write-protected"

Remark: This command is very error-tolerant: ecode will almost always be 0, even if invalid modelid or objid is passed. Only on the most severe errors, ecode will be 1.

# See Also:  



Example:




