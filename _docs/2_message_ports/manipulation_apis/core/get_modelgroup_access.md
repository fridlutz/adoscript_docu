---
layout: commandcall
category: CommandCall
title: "GET_MODELGROUP_ACCESS"
tags: 1.3 1.5
---

GET_MODELGROUP_ACCESS returns the access mode of the given user group on the given model group.

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_MODELGROUP_ACCESS	mgroupid:id usergroup:strValue
								singlesignon: 1|0


#--> RESULT ecode:intValue access:strValue .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`mgroupid`|intValue, the ID of the parent modelgroup|
|`usergroup`|strValue, the name of the user group; if singlesignon is non-zero, usergroup is interpreted as system user group name, otherwise usergroup is interpreted as ADOxx user group name. This means that if singlesignon is missing and the given usergroup is a system user group, an error will be returned.|
|`singlesignon`|1|0, is 1 if single-sign-on is active|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`access`|strValue, is set to either "none", "read" or "write", where "none" means no access to the modelgroup, "read" means readonly access and "write" means both read and write access.|

# Remarks:



# See Also:


