---
layout: commandcall
category: CommandCall
title: "DESELECT_ALL"
tags: 1.3 1.5
---

DESELECT_ALL resets the selection of all objects in one model.

# Syntax:  

```adoscript
{% raw %}
CC "Modeling" DESELECT_ALL [ modelid:intVal] .


# --> RESULT ecode:intValue .

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|intVal|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|


# Remarks:

The ID of the model is passed with modelid.  
If no modelid is given, the command resets the selection in the currently active model.  
A nonzero ecode value means that a model with the given ID is not opened.

Example:  
![](/images/DESELECT.png)

Activity "aktiv6" is selected, "aktiv5" is not.

Hint: does not work for tabular modeling.

# See Also:  



Example:




