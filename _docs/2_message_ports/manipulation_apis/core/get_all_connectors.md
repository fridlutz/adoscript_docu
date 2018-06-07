---
layout: commandcall
category: CommandCall
title: "GET_ALL_CONNECTORS"
tags: 1.3 1.5
---

GET_ALL_CONNECTORS returns a list of object ids (separated by spaces) of all connectors within a model.

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_ALL_CONNECTORS modelid:intVal .


#-->RESULT ecode:intValue objids:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|intVal, the argument modelid has to be set to the id of the model for which the connectors should be retrieved.|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`objids`|strValue, The return variable objids contains a list of connector ids separated by spaces.|

# Remarks:



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

# get all connectors of the model
CC "Core" GET_ALL_CONNECTORS modelid:(VAL modelid)

# for each connecor, dye it
FOR id in:(objids)
{
   CC "Modeling" DYE (VAL id) error-mark
}

{% endraw %}
```
{: .line-numbers}
First the id of the currently active model id retrieved. For this model, all connector ids are retrieved. in a FOR-loop, each connector is dyed.  
