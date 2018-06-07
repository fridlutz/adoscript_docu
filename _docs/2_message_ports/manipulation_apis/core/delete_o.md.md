---
layout: commandcall
category: CommandCall
title: "DELETE_OBJS"
tags: 1.3 1.5
---

DELETE_OBJS deletes a set of instances (modeling objects and/or connectors) at once. The objects must be of one model.

# Syntax:  

```adoscript
{% raw %}
CC "Core" DELETE_OBJS modelid:id objids:idList .


#-->RESULT ecode:intValue errobjs:idList
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|id, the ID of the model containing the instances to be deleted.|
|`objids`|idList, contains a space-separated list of instance IDs (IDs of modeling objects and/or connectors) to be deleted.|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`errobjs`|idList|

# Remarks:



# See Also:  



Example 1:

```adoscript
{% raw %}

SEND "GET_ACTIVE_MODEL" to:"Modeling" answer:modelid
SET mid:(VAL modelid)
CC "Core" GET_ALL_OBJS modelid:(mid)
CC "Core" DELETE_OBJS modelid:(mid) objids:(objids)
CC "Modeling" REBUILD_DRAWING_AREA modelid:(mid)

{% endraw %}
```
{: .line-numbers}

