---
layout: commandcall
category: CommandCall
title: "GET_ROOT_MODELGROUP_ID"
tags: 1.3 1.5
---

The command GET_ROOT_MODELGROUP_ID returns the mgroupid of the invisible toplevel modelgroup ID.

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_ROOT_MODELGROUP_ID

#--> RESULT ecode:intValue mgroupid:id
{% endraw %}
```
{: .line-numbers}

# Parameters:  

none

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`mgroupid`|intValue, the invisible toplevel modelgroup ID.|

# Remarks:



# See Also:  



Example 1:

```adoscript
{% raw %}

# get root modelgroup ID
CC "Core" GET_ROOT_MODELGROUP_ID

# get all visible top level groups
CC "Core" GET_MODELGROUP_CHILDREN mgroupid:(mgroupid)

CC "AdoScript" INFOBOX (submgroupids)

{% endraw %}
```
{: .line-numbers}

- get root modelgroup ID  
- get all subgroups  
- print list of IDs  
