---
layout: commandcall
category: CommandCall
title: "GET_MODELGROUP_CHILDREN"
tags: 1.3 1.5
---

GET_MODELGROUP_CHILDREN returns the IDs of all model groups that are contained in a certain (parent) modelgroup.

# Syntax:  

```adoscript
{% raw %}
CC Core" GET_MODELGROUP_CHILDREN [ mgroupid:id ] [ recursive ]

#--> RESULT ecode:intValue  submgroupids:strValue .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`mgroupid`|intValue, the ID of the parent model group. If mgroupid is not specified, the root model group is used!|
|`recursive`|modifier, if specified, all child model groups are evaluated recursively. If it is not specified, only the direct children of the parent model group are returned.|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`submgroupids`|strValue, token string containing the model group IDs separated by blanks|

# Remarks:



# See Also:  



Example 1:

Show complete model group structure in a view box  
```adoscript
{% raw %}

CC "Core" GET_ROOT_MODELGROUP_ID
SET s:""
GET_MODEL_GROUPS mgroupid:(mgroupid) level:0
CC "AdoScript" VIEWBOX text:(s)

PROCEDURE GET_MODEL_GROUPS mgroupid:integer level:integer {
    CC "Core" GET_MODELGROUP_NAME mgroupid:(mgroupid)
    SET s:(s + (level ** "    ") + mgroupname + " (" + STR mgroupid + ")\n")
    CC "Core" GET_MODELGROUP_CHILDREN mgroupid:(mgroupid) 
    FOR sid in:(submgroupids) {
        GET_MODEL_GROUPS mgroupid:(VAL sid) level:(level + 1)
    }
}

{% endraw %}
```
{: .line-numbers}

