---
layout: commandcall
category: CommandCall
title: "CHECK_POSITIONS_IN_VARIANT"
tags: 1.3 1.5
---

CHECK_POSITIONS_IN_VARIANT checks the position information of all objects in a certain variant and returns whether all, some or none of the objects do not have a position.

# Syntax:  

```adoscript
{% raw %}
CC "Drawing" CHECK_POSITIONS_IN_VARIANT	modelid:intValue variant:strValue

#--> RESULT ecode:intValue missing: "all" | "some" | "none"
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|intValue, the model whose object positions shall be checked|
|`variant`|strValue, the name of the variant where to check object positions|

# Returns:  

|`ecode`|intValue, 0 if the command call was successful, to 1 otherwise.|
|`missing`|strValue,|

# Remarks:

If the position is missing for all objects in the specified variant, the result variable missing is set to "all". If the position is missing for some (but not all) objects, the result is "some". If all objects have a position in the specified variant, missing is set to "none".

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Modeling" GET_ACT_MODEL  #--> modelid
CC "Drawing" CHECK_POSITIONS_IN_VARIANT modelid:(modelid) 
										variant:"Without swimlanes (horizontal)"
{% endraw %}
```
{: .line-numbers}

