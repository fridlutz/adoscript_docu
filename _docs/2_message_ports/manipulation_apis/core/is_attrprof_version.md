---
layout: commandcall
category: CommandCall
title: "IS_ATTRPROF_VERSION"
tags: 1.3 1.5
---

IS_ATTRPROF_VERSION checks whether the given ID (objid) is a valid AttrProf version ID.

# Syntax:  

```adoscript
{% raw %}
CC "Core" IS_ATTRPROF_VERSION objid:intValue . 


# --> RESULT is_apversion:[0|1]

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`objid`|intValue|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`is_apversion`|[0|1], The return value is 0 if the ID is not an AttrProf version and 1 if the ID uniquely identifies an AttrProf version.|

# Remarks:

Note: This functions does NOT return an ecode!

# See Also:  



Example:

