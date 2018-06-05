---
layout: commandcall
category: CommandCall
title: "DESELECT"
tags: 1.3 1.5
---

DESELECT resets the selection of one object.

# Syntax:  

```adoscript
{% raw %}
CC "Modeling" DESELECT objid:intVal .


# --> RESULT ecode:intValue .

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`objid`|intVal|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|


# Remarks:

The ID of the object is passed with objid.  
A nonzero ecode value means that the object could not be found.

Example:  
![](/images/DESELECT.png)

Activity "aktiv6" is selected, "aktiv5" is not.

Hint: does not work for tabular modeling.


# See Also:  



Example:




