---
layout: commandcall
category: CommandCall
title: "GET_MODELGROUPS_OF_MODELVERSION"
tags: 1.3 1.5
---

GET_MODELGROUPS_OF_MODELVERSION returns all modelgroups in which a modelversion is referenced.

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_MODELGROUPS_OF_MODELVERSION modelid:intValue

#--> RESULT ecode:intValue  mgroupids:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|intValue, the model version ID of which you want to retrieve the modelgroups.|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`mgroupids`|strValue, ID list separated by blank spaces.|

# Remarks:

This command makes no checks whether you have write or read access on the modelgroups!

# See Also:  



Example 1:

```adoscript
{% raw %}

# get the current model
SEND "GET_ACTIVE_MODEL" to:"Modeling" answer:modelid
IF (modelid = "")
{
  CC "AdoScript" ERRORBOX "Open a model first!"
  EXIT
}

CC "Core" debug GET_MODELGROUPS_OF_MODELVERSION modelid:(VAL modelid)

{% endraw %}
```
{: .line-numbers}

