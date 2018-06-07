---
layout: commandcall
category: CommandCall
title: "GET_CLASS_NAME"
tags: 1.3 1.5
---

GET_CLASS_NAME returns the name of a class.

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_CLASS_NAME classid:intValue

#--> RESULT ecode:intValue classname:strValue isrel:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`classid`|intValue, the ID of the class|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`classname`|strValue, the name of the given class|
|`isrel`|intValue, is set to 1 it the class is a relationclass, to 0 if it is not.|

# Remarks:



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

# from the list of selected objects, extract the first objectid
SET firstselected:(token(objids,0," "))

# get the classid of the class of the object
CC "Core" GET_CLASS_ID objid:(VAL firstselected)

# get the classname
CC "Core" GET_CLASS_NAME classid:(classid)

# print the id in an infobox
IF (isrel = 1)
{
   CC "AdoScript" INFOBOX ("You selected an object of the relationclass " + classname)
}
ELSE
{
   CC "AdoScript" INFOBOX ("You selected a connector the class " + classname)
}

{% endraw %}
```
{: .line-numbers}
Before you execute this example, open a model and select an object or a connector within the model. Then execute the script: the script retrieves the id of the selected object. Then with GET_CLASS_ID it gets the id of the class and the type (is it a relation or a class) of the selected object. Finally it prints a message with the retrieved name.

