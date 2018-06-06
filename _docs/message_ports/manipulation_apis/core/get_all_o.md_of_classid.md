---
layout: commandcall
category: CommandCall
title: "GET_ALL_OBJS_OF_CLASSID"
tags: 1.3 1.5
---

The command GET_ALL_OBJS_OF_CLASSID retrieves all instances (not relations!) of the given class ID in the given model!

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_ALL_OBJS_OF_CLASSID modelid:id classid:id


#-->RESULT ecode:intValue objids:list
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|id, the parameter modelid specifies the model from which we want the instances.|
|`classid`|id, the parameter classid specified the lookup class.|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`objids`|list|

# Remarks:



# See Also:  



Example 1:

```adoscript
{% raw %}

# get current model
SEND "GET_ACTIVE_MODEL" to:"Modeling" answer:modelid

IF (LEN (modelid) = 0)
{
  CC "AdoScript" ERRORBOX ("Please open a model!")
  EXIT
}

SET clname:"Aktivität"

CC "Core" GET_CLASS_ID classname:(clname)
SET clid:(classid)

IF (ecode != 0)
{
  CC "AdoScript" ERRORBOX ("There is no class '" + (clname) + "'!")
  EXIT
}

# get all objs of class
CC "Core" GET_ALL_OBJS_OF_CLASSID modelid:(VAL modelid) classid:(clid)

IF (LEN (objids) = 0)
{
  CC "AdoScript" ERRORBOX ("You have no instances of class '" + (clname) + "'!")
  EXIT
}

# get name of first object
CC "Core" GET_OBJ_NAME objid:(VAL token (objids, 0, " "))

CC "AdoScript" INFOBOX ("First 'Aktivität' found is called '" + (objname) + "'")

{% endraw %}
```
{: .line-numbers}
- get active model's id  
- determine ID of class 'Aktivität'  
- determine all instances of class 'Aktivität'  
- check if any instance was found  
- get name of first instance and show infobox  
