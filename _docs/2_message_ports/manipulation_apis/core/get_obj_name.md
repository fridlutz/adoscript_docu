---
layout: commandcall
category: CommandCall
title: "GET_OBJ_NAME"
tags: 1.3 1.5
---

The command GET_OBJ_NAME retrieves the name of an instance. This instance must exist in any loaded model - which one is determined automatically!

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_OBJ_NAME objid:id

#-->RESULT ecode:intValue objname:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`objid`|id|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`objname`|strValue|

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

# get all objs of class
CC "Core" GET_ALL_OBJS_OF_CLASSNAME modelid:(VAL modelid) classname:"Aktivität"

IF (LEN (objids) = 0)
{
  CC "AdoScript" ERRORBOX ("You have no instances of class 'Aktivität'!")
  EXIT
}

# get name of first object
CC "Core" GET_OBJ_NAME objid:(VAL token (objids, 0, " "))

CC "AdoScript" INFOBOX ("First 'Aktivität' found is called '" + (objname) + "'")

{% endraw %}
```
{: .line-numbers}
- get active model's id  
- determine all instances of class "Aktivität"  
- check if any instance was found  
- get name of first instance and show infobox  
