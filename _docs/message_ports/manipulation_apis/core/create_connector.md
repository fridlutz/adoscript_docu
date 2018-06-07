---
layout: commandcall
category: CommandCall
title: "CREATE_CONNECTOR"
tags: 1.3 1.5
---

CREATE_CONNECTOR creates a new connector between two instance in a model. The model has to be loaded first.

# Syntax:  

```adoscript
{% raw %}
CC "Core" CREATE_CONNECTOR modelid:intValue fromobjid:intValue toobjid:intValue classid:intValue 

#-->RESULT ecode:intValue objid:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|intValue, the id of the model|
|`fromobjid`|intValue, id of the source instance|
|`toobjid`|intValue, id of the target instance|
|`classid`|intValue, id of the relationclass specifying which type of connector should be created|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`objid`|intValue, the id of the newly created connector.|

# Remarks:

In ADOxx connectors always have a direction, pointing from source to target instance.

# See Also:  



Example 1:

```adoscript
{% raw %}

# get all selected objects
CC "Modeling" GET_SELECTED
IF (objids = "")
{
   CC "AdoScript" ERRORBOX "No object has been selected!"
   EXIT
}


# from the list of selected objects, extract the first and second objectid
SET firstselected:(VAL token(objids,0," "))
SET secondselected:(VAL token(objids,1," "))

# get the id of the relationclass Nachfolger
CC "Core" GET_CLASS_ID relation classname:"Nachfolger"
IF (ecode != 0)
{
   CC "AdoScript" ERRORBOX "Your library does not contain a class called Nachfolger!\n"
   EXIT
}

# get the modelid of the current model
SEND "GET_ACTIVE_MODEL" to:"Modeling" answer:modelid
IF (modelid = "")
{
   CC "AdoScript" ERRORBOX "Open a new model first!"
   EXIT
}

CC "Core" CREATE_CONNECTOR modelid:(VAL modelid) classid:(classid)
                           fromobjid:(firstselected) toobjid:(secondselected) 

CC "Modeling" REBUILD_DRAWING_AREA

{% endraw %}
```
{: .line-numbers}
In the currently opened model, get the two first selected objects and create a "Nachfolger" relation between them.  
