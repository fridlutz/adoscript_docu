---
layout: commandcall
category: CommandCall
title: "SELECT_ALL"
tags: 1.3 1.5
---

SELECT_ALL sets all objects in a model selected. All previous selections will stay selected.

# Syntax:  

```adoscript
{% raw %}
CC "Modeling" SELECT_ALL  [ modelid:intVal ] [ with-swimlanes ] .


# --> RESULT ecode:intValue .

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|intVal|
|`with-swimlanes`|modifier|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|


# Remarks:

The ID of the model whose objects shall be selected is passed with modelid. If modelid is not specified, SELECT_ALL is applied to the active model window.

Example:  
![](/images/DESELECT.png)

Activity "aktiv6" is selected, "aktiv5" is not.

Hint: does not work for tabular modeling.


# See Also:  



Example:




