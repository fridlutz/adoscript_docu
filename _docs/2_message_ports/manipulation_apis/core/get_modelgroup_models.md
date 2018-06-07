---
layout: commandcall
category: CommandCall
title: "GET_MODELGROUP_MODELS"
tags: 1.3 1.5
---

GET_MODELGROUP_MODELS retrieves the IDs of all modelthreads or modelversions in a specific modelgroup.

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_MODELGROUP_MODELS mgroupid:id  [ getversionids ]

#--> RESULT ecode:intValue modelids:idlist
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`mgroupid `|intValue, specifies the modelgroup to search.|
|`getversionids `|modifier, indicates that you want version IDs as result.|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`modelids`|intValue, contains the IDs as a space-separated string.|

# Remarks:



# See Also:  



Example:

