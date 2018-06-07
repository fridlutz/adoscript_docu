---
layout: commandcall
category: CommandCall
title: "IS_ATTRPROF_CLASS"
tags: 1.3 1.5
---

IS_ATTRPROF_CLASS checks whether the given ID (classid) specifies an AttriProf class.

# Syntax:  

```adoscript
{% raw %}
CC "Core" IS_ATTRPROF_CLASS classid:intValue . 


#--> RESULT is_apclass:[0|1]

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`classid`|intValue|

# Returns:  

|`is_apclass`|[0|1], the return value 0 means the ID is not an AttrProf class, and 1 means that this ID is an AttrProf class.|

# Remarks:

Note: This functions does NOT return an ecode!

# See Also:  



Example:

