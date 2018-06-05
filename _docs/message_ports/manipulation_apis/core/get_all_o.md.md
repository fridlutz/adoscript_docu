---
layout: commandcall
category: CommandCall
title: "GET_ALL_OBJS"
tags: 1.3 1.5
---

GET_ALL_OBJS returns a list of all object ids (separated by spaces) with in the model.

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_ALL_OBJS modelid:id .


#-->RESULT ecode:intValue objids:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|id, the id of the model is specified with the argument modelid.|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`objids`|strValue, the list of objects is returned in the variable objids.|

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

# get all objects
CC "Core" GET_ALL_OBJS modelid:(VAL modelid)
IF (ecode != 0)
{
   CC "AdoScript" ERRORBOX "Something went very wrong here (e.g. we passed the wrong model id)!\n"
   EXIT
}

# for each object...
FOR id in:(objids)
{
   # ... get the classid and with that the classname
   CC "Core" GET_CLASS_ID objid:(VAL id)
   CC "Core" GET_CLASS_NAME classid:(classid)

   # and if the class is an "Aktivität", select it
   IF (classname = "Aktivität")
   {
      CC "Modeling" DYE (VAL id) error-mark 
   }
}

{% endraw %}
```
{: .line-numbers}
Retrieves ids of all objects in the current model. For each object, checks if its classname and if it is of class "Aktivität", selects it.  
