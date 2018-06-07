---
layout: commandcall
category: CommandCall
title: "EXEC_LAYOUT_ALGORITHM"
tags: 1.3 1.5
---

EXEC_LAYOUT_ALGORITHM applies a layout algorithm on a model.

# Syntax:  

```adoscript
{% raw %}
CC "Drawing" EXEC_LAYOUT_ALGORITHM	name:strValue modelid:intValue

# --> RESULT ecode:intValue 
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`name`|strValue, specifies the algorithm which shall be applied on this model|
|`modelid`|intValue, specifies the ID of the model|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|


# Remarks:

A layout algorithm with the specified name must exist. It can be statically customized or dynamically created with  CC "Drawing" CREATE_LAYOUT_ALGORITHM. Note that the UI independent name has to be used here.

# See Also:  

[CREATE_LAYOUT_ALGORITHM](create_layout_algorithm.html "CREATE_LAYOUT_ALGORITHM")  


Example 1:

```adoscript
{% raw %}

CC "Modeling" GET_ACT_MODEL
SET algname:"Without swimlanes (horizontal)"
CC "Drawing" EXEC_LAYOUT_ALGORITHM name:(algname) modelid:(modelid)

{% endraw %}
```
{: .line-numbers}

