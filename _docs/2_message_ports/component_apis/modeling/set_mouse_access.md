---
layout: commandcall
category: CommandCall
title: "SET_MOUSE_ACCESS"
tags: 1.3 1.5
---

SET_MOUSE_ACCESS locks or unlocks the mouse access on all objects of a class in a model or on a single object.

# Syntax:  

```adoscript
{% raw %}
CC "Modeling"
SET_MOUSE_ACCESS	ObjSpec [ access:boolVal ] .


ObjSpec :	ClassByName | SingleObj .


ClassByName :	[ modelid:id ] classname:strValue .



SingleObj :	objid:intValue .

{% endraw %}
```
{: .line-numbers}

```adoscript
{% raw %}
# --> RESULT ecode:intValue .

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|id|
|`classname`|strValue|
|`objid`|intValue|
|`access`|boolVal|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|


# Remarks:

SET_MOUSE_ACCESS should not be used to implement view modes (variants). Use SET_OBJ_VISIBLE instead.

# See Also:  

[SET_OBJ_VISIBLE](set_obj_visible.html "SET_OBJ_VISIBLE")  


Example 1:

```adoscript
{% raw %}

CC "Modeling" GET_SELECTED
FOR objid in:(objids) {
    CC "Modeling" SET_MOUSE_ACCESS objid:(VAL objid) access:0
}

{% endraw %}
```
{: .line-numbers}


