---
layout: commandcall
category: CommandCall
title: "SET_MODELGROUP_ACCESS"
tags: 1.3 1.5
---

SET_MODELGROUP_ACCESS changes the access mode of a usergroup on a modelgroup.

# Syntax:  

```adoscript
{% raw %}
CC "Core" SET_MODELGROUP_ACCESS mgroupid:id usergroup:strValue
								singlesignon:1|0 
								access: strValue

#--> RESULT ecode:intValue .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`mgroupid`|intValue, he ID of the model group|
|`usergroup`|strValue, the name of the user group;  If singlesignon is true (i.e. it is specified without value or with nonzero value), usergroup is interpreted as system user group name, otherwise (not specified or with value 0) usergroup is interpreted as ADOxx user group name.|
|`singlesignon`|1|0|
|`access`|strValue; the value can be either "none", "read" or "write". If anything else is passed, the value "none" is used.|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|

# Remarks:



# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Core" GET_MODELGROUP_ID mgroupname:"Modelle" sep:"\t"
CC "Core" SET_MODELGROUP_ACCESS
        mgroupid:(mgroupid) usergroup:"ADOxx" access:"write"
CC "Core" SET_MODELGROUP_ACCESS
        mgroupid:(mgroupid) usergroup:"BOC" singlesignon access:"read"

{% endraw %}
```
{: .line-numbers}

