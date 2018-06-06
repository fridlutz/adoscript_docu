---
layout: commandcall
category: CommandCall
title: "GET_MODEL_BASENAME"
tags: 1.3 1.5
---

GET_MODEL_BASENAME returns the basename of a model.

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_MODEL_BASENAME modelid:intValue

#-->RESULT ecode:intValue basename:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|intValue, the id of the model|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success|
|`basename`|strValue, the name of the model.|

# Remarks:



# See Also:  



Example 1:

Retrieve the name of the current model  
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
CC "Core" GET_MODEL_BASENAME modelid:(VAL modelid)

# tell the user the modeltype of the current model
CC "AdoScript" INFOBOX ("The current model is called: " + basename)

{% endraw %}
```
{: .line-numbers}

