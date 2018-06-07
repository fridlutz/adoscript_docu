---
layout: commandcall
category: CommandCall
title: "SET_OBJ_VISIBLE"
tags: 1.3 1.5
---

SET_OBJ_VISIBLE shows or hides a single object. This makes it possible to program view modes which not just work on class level. View modes which work on object level are also called variants.

# Syntax:  

```adoscript
{% raw %}
CC "Modeling" SET_OBJ_VISIBLE objid:id [ visible:boolVal ] .


# --> RESULT ecode:intValue .

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`objid`|id|
|`visible`|boolVal|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|


# Remarks:

See also: SET_ALL_OBJS_VISIBLE.  
The single object visibility is independent of the view mode visibility. That means if an object has been hidden by SET_OBJ_VISIBLE with visible:0 it just can be shown again by SET_OBJ_VISIBLE with visible:1. An object which is invisible in the current view mode can not be shown by SET_OBJ_VISIBLE.  
Hidden objects are not accessable. It is not needed to lock the mouse access for them.

# See Also:  

[SET_ALL_OBJS_VISIBLE](set_all_objs_visible.html "SET_ALL_OBJS_VISIBLE")  


Example 1:

```adoscript
{% raw %}

CC "Modeling" GET_SELECTED
FOR objid in:(objids) {
    CC "Modeling" SET_OBJ_VISIBLE objid:(VAL objid) visible:0
}

{% endraw %}
```
{: .line-numbers}


