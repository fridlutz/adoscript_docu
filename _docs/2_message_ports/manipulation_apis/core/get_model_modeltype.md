---
layout: commandcall
category: CommandCall
title: "GET_MODEL_MODELTYPE"
tags: 1.3 1.5
---

GET_MODEL_MODELTYPE returns the modeltype of a model.

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_MODEL_MODELTYPE modelid:intValue

#--> RESULT ecode:intValue modeltype:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|intValue, the ID of the model|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`modeltype`|strValue, the modeltype of the given model|

# Remarks:



# See Also:  



Example 1:

Retrieve the modeltype of the current model  
```adoscript
{% raw %}

# get the id of the current model
SEND "GET_ACTIVE_MODEL" to:"Modeling" answer:modelid
IF (modelid = "")
{
   CC "AdoScript" ERRORBOX "Open a model first!"
   EXIT
}

# get the modeltype of the model
CC "Core" GET_MODEL_MODELTYPE modelid:(VAL modelid)

# tell the user the modeltype of the current model
CC "AdoScript" INFOBOX ("The current model is of modeltype: " + modeltype)

{% endraw %}
```
{: .line-numbers}

