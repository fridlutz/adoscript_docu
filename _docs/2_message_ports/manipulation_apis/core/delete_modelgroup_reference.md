---
layout: commandcall
category: CommandCall
title: "DELETE_MODELGROUP_REFERENCE"
tags: 1.3 1.5
---

DELETE_MODELGROUP_REFERENCE deletes the specified modelgroup reference.

# Syntax:  

```adoscript
{% raw %}
CC "Core" DELETE_MODELGROUP_REFERENCE refid:intValue

#--> RESULT ecode:intValue .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`refid`|intValue, id of the refefrence to be deleted|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|

# Remarks:

This ID is unqiue for all modelgroups so there is no need for further parameters.

Returns CLASSINSTANCE_NOT_EXISTING if the given reference ID (refid) is invalid.

Returns SAVE_NOT_ALLOWED if you have no write premissions on the modelgroup to which the reference belongs.

# See Also:  

[COPY_MODELGROUP_REFERENCE](copy_modelgroup_reference.html "COPY_MODELGROUP_REFERENCE")  


