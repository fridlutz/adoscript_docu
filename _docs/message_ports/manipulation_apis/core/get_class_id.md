---
layout: commandcall
category: CommandCall
title: "GET_CLASS_ID"
tags: 1.3 1.5
---

GET_CLASS_ID returns the ID of a class.

# Syntax:  

GetClassIDByClasslName  
```adoscript
{% raw %}
CC "Core" GET_CLASS_ID [ relation ] classname:strValue [ bp-library | we-library ]

#--> RESULT ecode:intValue classid:intValue
{% endraw %}
```
{: .line-numbers}

GetClassIDByObject  
```adoscript
{% raw %}
GET_CLASS_ID objid:id .

#--> RESULT ecode:intValue classid:intValue isrel:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`classname`|strValue, the name of the class|
|`objid`|intValue, the ID of the object whose class ID is requested|
|`relation`|modifier, specifies that the class having the given name is a relation|
|`bp-library`|modifier, if specified, the id is retrieved from a class in the ADOxx Dynamic Library|
|`we-library`|modifier, if specified, the id is retrieved from a class in the ADOxx Static Library|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`classid`|intValue, the requested class ID|
|`isrel`|intValue, is 1 if the class is a relation and 0 otherwise.|

# Remarks:



# See Also:  

[GET_CLASS_NAME](get_class_name.html "GET_CLASS_NAME")  


Example 1:

Create a new instance of the class "A"  
```adoscript
{% raw %}

# get the classid of activity
CC "Core" GET_CLASS_ID classname:"A"
IF (ecode != 0)
{
   CC "AdoScript" ERRORBOX "Your library does not contain a class called A!\n"
   EXIT
}

# get the modelid of the current model
SEND "GET_ACTIVE_MODEL" to:"Modeling" answer:modelid
IF (modelid = "")
{
   CC "AdoScript" ERRORBOX "Open a new model first!"
   EXIT
}

# create the object
CC "Core" CREATE_OBJ modelid:(VAL modelid) classid:(classid) objname:"A new activity"
IF (ecode != 0)
{
   CC "AdoScript" ERRORBOX ("The object could not be created. \n"+
                            "Maybe one with the same name already exists?")
}

# this has to be called to update the modeling window
CC "Modeling" REBUILD_DRAWING_AREA


{% endraw %}
```
{: .line-numbers}
Open a new model and execute the script. The script retrieves the id of the class "Aktivit�t" and the id of the model. With these ids it creates a new instance of the class.

Example 2:

When passing the id of an object with the argument objid, the command GET_CLASS_ID returns the class of the object in the return variable classid. The second return variable isrel is set to 1 if the class is a relationclass, to 0 if it is a common class.

Get class of the currently selected object/connector  
```adoscript
{% raw %}

# get all selected objects
CC "Modeling" GET_SELECTED
IF (objids = "")
{
   CC "AdoScript" ERRORBOX "No object has been selected!"
   EXIT
}

# from the list of selected objects, extract the first objectid
SET firstselected:(token(objids,0," "))

# get the classid of the class of the object
CC "Core" GET_CLASS_ID objid:(VAL firstselected)

# print the id in an infobox
IF (isrel = 1)
{
   CC "AdoScript" INFOBOX ("You selected a connector with the relation " + STR classid)
}
ELSE
{
   CC "AdoScript" INFOBOX ("You selected an object with the class " + STR classid)
}

{% endraw %}
```
{: .line-numbers}
Before you execute this example, open a model and select an object or a connector within the model. Then execute the script: the script retrieves the id of the selected object. Then with GET_CLASS_ID it gets the id of the class and the type (is it a relation or a class) of the selected object. Finally it prints a message with the retrieved id.

