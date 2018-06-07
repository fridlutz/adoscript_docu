---
layout: commandcall
category: CommandCall
title: "IS_ATTRPROF_THREAD"
tags: 1.3 1.5
---

IS_ATTRPROF_THREAD checks whether the given ID (objid) is a valid AttrProf thread ID.

# Syntax:  

```adoscript
{% raw %}
CC "Core" IS_ATTRPROF_THREAD objid:intValue . 


# --> RESULT is_apthread:[0|1]

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`objid`|intValue|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`is_apthread`|[0|1], the return value is 0 if the ID is not an AttrProf thread and 1 if the ID uniquely identifies an AttrProf thread.|

# Remarks:

Note: This functions does NOT return an ecode!

# See Also:  



Example:

