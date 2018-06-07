---
layout: commandcall
category: CommandCall
title: "SET_FOCUS_NODE"
tags: 1.3 1.5
---

SET_FOCUS_NODE sets the focus to the node specified with the argument objid.

# Syntax:  

```adoscript
{% raw %}
CC "Modeling" SET_FOCUS_NODE objid:intValue .

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`objid`|intValue|

# Returns:  

none


# Remarks:



Example: Activity "aktiv5" recieved the focus.

![](/images/SET_FOCUS_NODE.png)

Returns an error when the intVal passed in the argument objid is not valid or not the id of a node.

# See Also:  



Example 1:

```adoscript
{% raw %}

SEND "GET_ACTIVE_MODEL" to:"Modeling" answer:modelid

CC "Core" GET_ALL_OBJS modelid:(VAL modelid)

FOR objid in:(objids)
{
   CC "Modeling" SET_FOCUS_NODE objid:(VAL objid)
   CC "AdoScript" SLEEP ms:1000
}

{% endraw %}
```
{: .line-numbers}
The example gets all objects in the current model and then focuses one after the other for one second.

