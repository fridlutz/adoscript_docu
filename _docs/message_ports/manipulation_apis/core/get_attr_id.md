---
layout: commandcall
category: CommandCall
title: "GET_ATTR_ID"
tags: 1.3 1.5
---

GET_ATTR_ID returns the ID of an attribute.  

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_ATTR_ID classid:ClassID attrname:strValue .


ClassID :	id | bp-model | we-model .


#-->RESULT ecode:intValue attrid:id
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`classid`|ClassID|
|`attrname`|strValue|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`attrid`|id|

# Remarks:

The name of the attribute has to be passed in the argument attrname and the id of the class has to be passed with the argument classid. When you want to retrieve the id of a modelattribute, pass bp-model or we-model in the argument classid.

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
SET selected:(VAL token(objids,0," "))

# get the class of the selected object
CC "Core" GET_CLASS_ID objid:(selected)

# get the attribute "Name" of the class
CC "Core" GET_ATTR_ID classid:(classid) attrname:"Name"
IF (ecode != 0)
{
   CC "AdoScript" ERRORBOX "The selected object does not contain an attribute called \"Name\"!"
   EXIT
}

# set the name of the selected object
CC "Core" SET_ATTR_VAL objid:(selected) attrid:(attrid) val:"Seppl"
IF (ecode != 0)
{
   CC "AdoScript" ERRORBOX "Could not set the attribute value!"
   EXIT
}

{% endraw %}
```
{: .line-numbers}
Renames the selected object to "Seppl".  
