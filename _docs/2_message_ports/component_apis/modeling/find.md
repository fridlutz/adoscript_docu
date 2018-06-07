---
layout: commandcall
category: CommandCall
title: "FIND"
tags: 1.3 1.5
---

FIND marks one object as if it has been selected by clicking on it with the mouse.  
All previous selections are being deselected.

# Syntax:  

```adoscript
{% raw %}
CC "Modeling" FIND objid:intVal .


# --> RESULT ecode:intValue .

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`objid`|intVal, the ID of the object that shall be selected is passed with objid.|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|


# Remarks:

A nonzero ecode value means that a model with the given ID is not opened.

Example:  
![](/images/DESELECT.png)

Activity "aktiv6" is selected, "aktiv5" is not.

Hint: does not work for tabular modeling.

# See Also:  



Example:




