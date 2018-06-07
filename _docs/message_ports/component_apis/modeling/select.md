---
layout: commandcall
category: CommandCall
title: "SELECT"
tags: 1.3 1.5
---

SELECT marks one object as if it has been selected by clicking on it with the mouse.

# Syntax:  

```adoscript
{% raw %}
CC "Modeling" SELECT objid:intVal .


# --> RESULT ecode:intValue .

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`objid`|intVal|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|


# Remarks:

The ID of the object that shall be selected is passed with objid. All previous selections will stay selected.

Example:  
![](/images/DESELECT.png)

Activity "aktiv6" is selected, "aktiv5" is not.

Hint: does not work for tabular modeling.

# See Also:  



Example:




