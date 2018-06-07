---
layout: commandcall
category: CommandCall
title: "GET_MODELGROUP_REFERENCES"
tags: 1.3 1.5
---

GET_MODELGROUP_REFERENCES retrieves all modelgroup-references of the given modelgroup (mgroupid).

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_MODELGROUP_REFERENCES mgroupid:intValue

#--> RESULT ecode:intValue refids:strValue .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`mgroupid`|intValue, specifies the ID of the modelgroup|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`refids`|strValue, a space-separated list of IDs grouped into a string|

# Remarks:

returns CLASS_NOT_EXISTING if the given modelgroup ID (mgroupid) is invalid.

# See Also:  



