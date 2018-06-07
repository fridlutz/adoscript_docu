---
layout: commandcall
category: CommandCall
title: "GET_OBJ_ID"
tags: 1.3 1.5
---

GET_OBJ_ID retrieves the id of an instance / an object.

# Syntax:  

```adoscript
{% raw %}
GetObjectID :	GetObjIDByObjName | GetObjIDByObjIDs

{% endraw %}
```
{: .line-numbers}

```adoscript
{% raw %}
GetObjIDByObjName :	CC "Core" GET_OBJ_ID modelid:id classid:id objname:strValue .

{% endraw %}
```
{: .line-numbers}

```adoscript
{% raw %}
GetObjIDByObjIDs :	CC "Core" GET_OBJ_ID modelid:id classid:id objid1:id objid2:id .

{% endraw %}
```
{: .line-numbers}


```adoscript
{% raw %}
#-->RESULT ecode:intValue objid:id
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|id|
|`classid`|id|
|`objname`|strValue|
|`modelid`|id|
|`classid`|id|
|`objid1`|id|
|`objid2`|id|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`objid`|id|

# Remarks:

The objectid can be retrieved by specifying the name of the object. Alternatively the id of connectors can be retrieved by specifying two object ids (for the from- and the to-object).

To retrieve the objectid by name, the name of the instance has to be passed with the argument objname. The id of the model has to be passed with the argument modelid and the id of the class of the object has to be passed with the argument classid.

To retrieve the objectid of a connector, the ids of the two instances that are connected by the connector have to be passed with the arguments objid1 and objid2.

# See Also:  



Example 1:

```adoscript
{% raw %}

SEND "GET_ACTIVE_MODEL" to:"Modeling" answer:modelid
IF (modelid = "")
{
   CC "AdoScript" ERRORBOX "Open a model first"
   EXIT
}

CC "Core" GET_CLASS_ID classname:"Aktivität"
IF (ecode != 0)
{
   CC "AdoScript" ERRORBOX "Your library does not contain a class called Aktivität!\n"
   EXIT
}

CC "Core" GET_OBJ_ID modelid:(VAL modelid) classid:(classid) objname:"Sepp"
IF (ecode != 0)
{
   CC "AdoScript" INFOBOX ("Your model does not contain an activity called \"Sepp\"!\n"+
                           "Please model one and then rerun the script.")
}
ELSE
{
   CC "AdoScript" INFOBOX ("Activity \"Sepp\" was found, id=" + STR objid)
}

{% endraw %}
```
{: .line-numbers}
Before you execute this example, open a new model. The script tries to retrieve the object id of an object called "Sepp!" of the class "Aktivität".

Example 2:

```adoscript
{% raw %}

# get all selected objects
CC "Modeling" GET_SELECTED
IF (objids = "")
{
   CC "AdoScript" ERRORBOX "No object has been selected!"
   EXIT
}

# get the id of the relationclass Nachfolger
CC "Core" GET_CLASS_ID relation classname:"Nachfolger"
IF (ecode != 0)
{
   CC "AdoScript" ERRORBOX "Your library does not contain a class called Nachfolger!\n"
   EXIT
}

# from the list of selected objects, extract the first and second objectid
SET firstselected:(VAL token(objids,0," "))
SET secondselected:(VAL token(objids,1," "))

# get the modelid containg the selected object
CC "Core" GET_MODEL_ID objid:(firstselected)

# now get the connector
CC "Core" GET_OBJ_ID modelid:(modelid) classid:(classid) objid1:(firstselected) objid2:(secondselected)
IF (ecode != 0)
{
   CC "Core" GET_OBJ_ID modelid:(modelid) classid:(classid) objid1:(secondselected)
                                                            objid2:(firstselected)
}

# did we find one?
IF (ecode != 0)
{
   CC "AdoScript" INFOBOX "The two instances you selected are not connected by Nachfolger"
}
ELSE
{
   CC "Modeling" DESELECT_ALL
   CC "Modeling" FIND objid:(objid)
}

{% endraw %}
```
{: .line-numbers}
Before you execute this example, open a model and select two objects that are connected by a "Nachfolger" relation.  
The script collects all necessary information (modelid, classid, ids of the selected objects) and then tries to get the relation that connects the two relations with the command GET_OBJ_ID. If no connector was found pointing from the first selected object to the second selected object, GET_OBJ_ID is called a second time to search for connectors pointing from second to first selected object.  
If no connector was found, a message is displayed. If one was found, all objects are deselected and the connector is marked selected.  
