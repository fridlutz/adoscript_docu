---
layout: commandcall
category: CommandCall
title: "GET_MODELGROUPS_OF_MODELTHREAD"
tags: 1.3 1.5
---

GET_MODELGROUPS_OF_MODELTHREAD returns all modelgroups in which a modelthread is referenced.

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_MODELGROUPS_OF_MODELTHREAD threadid:intValue

#--> RESULT ecode:intValue  mgroupids:strValue .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`threadid`|intValue, the model thread ID of which you want to retrieve the modelgroups.|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`mgroupids`|strValue, ID list separated by blank spaces.|

# Remarks:

This command makes no checks whether you have write or read access on the modelgroups!


# See Also:  



Example:

