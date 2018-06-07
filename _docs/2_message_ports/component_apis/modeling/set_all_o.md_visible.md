---
layout: commandcall
category: CommandCall
title: "SET_ALL_OBJS_VISIBLE"
tags: 1.3 1.5
---

SET_ALL_OBJS_VISIBLE sets the single object visibility (see SET_OBJ_VISIBLE) for all objects of a model.

# Syntax:  

```adoscript
{% raw %}
CC "Modeling" SET_ALL_OBJS_VISIBLE [ modelid:id ] [ visible:boolVal ] .


# --> RESULT ecode:intValue .

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|id|
|`visible`|boolVal|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|


# Remarks:

The single object visibility is independent of the view mode visibility. That means if an object has been hidden by SET_OBJ_VISIBLE or SET_ALL_OBJS_VISIBLE with visible:0 it just can be shown again by SET_OBJ_VISIBLE or SET_ALL_OBJS_VISIBLE with visible:1. An object which is invisible in the current view mode can not be shown by SET_OBJ_VISIBLE or SET_ALL_OBJS_VISIBLE.  
Hidden objects are not accessable. It is not needed to lock the mouse access for them.

# See Also:  

[SET_OBJ_VISIBLE](set_obj_visible.html "SET_OBJ_VISIBLE")  


Example 1:

```adoscript
{% raw %}

CC "Modeling" SET_ALL_OBJS_VISIBLE visible:0

{% endraw %}
```
{: .line-numbers}


