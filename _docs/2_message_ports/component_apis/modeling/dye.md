---
layout: commandcall
category: CommandCall
title: "DYE"
tags: 1.3 1.5
---

DYE colors the outline of an object or a connector.

# Syntax:  

```adoscript
{% raw %}
CC "Modeling" DYE intValue [ error-mark ] [ set-value:intValue ] [ make-visible ]
{% endraw %}
```
{: .line-numbers}


# Parameters:  

|`error-mark`|modifier|
|`set-value`|intValue|
|`make-visible`|modifier|

# Returns:  

none

# Remarks:

The instance id of the object is passed in intVal. If no modelid is passed, the current active model will be taken.

Example: Activity "aktiv5" is outlined, "aktiv6" is not.

![](/images/DYE.png)

When calling DYE with the argument error-mark passed, the user can afterwards remove the outline by selecting the object. The outline can also be removed by calling UNDYE and passing the argument error-mark.

When error-mark is not passed for DYE, the user can not remove the outline himself. For each object an internal counter is held. The outline is displayed, when the value of the counter is greater than 0. Each call of DYE increases the counter and each call of UNDYE or UNDYE_ALL decreases it. The internal counter of an object can be directly set with DYE and the argument set-value.

When the argument make-visible is passed for a call to DYE, the specified object is made visible in the modeling window: if necessary the window scrolls so that the object is visible for the user.

# See Also:  



Example 1:

```adoscript
{% raw %}

SEND "GET_ACTIVE_MODEL" to:"Modeling" answer:modelid

CC "Core" GET_ALL_OBJS modelid:(VAL modelid)

FOR objid in:(objids)
{
   CC "Modeling" DYE (VAL objid) error-mark
}

CC "AdoScript" INFOBOX "Now all objects should be outlined"

CC "Modeling" UNDYE_ALL modelid:(VAL modelid)

{% endraw %}
```
{: .line-numbers}
The example marks all objects of the currently opened model, displays a infobox so that the user can see the outlined objects and then removes the outlines again.

