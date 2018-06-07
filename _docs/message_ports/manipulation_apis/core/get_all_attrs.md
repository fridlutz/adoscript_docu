---
layout: commandcall
category: CommandCall
title: "GET_ALL_ATTRS"
tags: 1.3 1.5
---

GET_ALL_ATTRS returns a list of attribute ids (separated by spaces).

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_ALL_ATTRS OfModelType | OfClass .


OfModelType :	modeltype:strValue [ with-hidden-attrs ] .


OfClass :	classid:intValue [ without-iattrs ] [ with-cattrs ]


#-->RESULT ecode:intValue attrids:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modeltype`|strValue|
with-hidden-attrs
|`classid`|intValue|
without-iattrs
with-cattrs

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`attrids`|strValue|

# Remarks:

If the name of a modeltype is passed in the argument modeltype, model attributes are returned. By default, hidden attributes are excluded. Specifying with-hidden-attrs lets the hidden attributes be included.

If the ID of a class is passed in the argument classid, instance attributes are retrieved. If the optional argument with-cattrs is passed, also IDs of class attributes will be returned. If both arguments without-iattrs and with-cattrs are passed, only class attribute IDs are returned.

# See Also:  



Example 1:

```adoscript
{% raw %}

# get the current active model
SEND "GET_ACTIVE_MODEL" to:"Modeling" answer:modelid

# get the modelthread of the modelversion (returned as String!)
CC "Core" GET_MODEL_THREAD_OF_VERSION modelversionid:(VAL modelid)

# get the modeltype of the current model
CC "Core" GET_MODEL_MODELTYPE modelid:(modelthreadid)

# get all modelattributes of the modeltype
CC "Core" GET_ALL_ATTRS modeltype:(modeltype) with-hidden-attrs

SET allattrnames:""
FOR id in:(attrids) {
   CC "Core" GET_ATTR_NAME attrid:(VAL id)
   IF (LEN allattrnames > 0) {
      SET allattrnames:(allattrnames + ", ")
   }
   SET allattrnames:(allattrnames + attrname)
}

CC "AdoScript" INFOBOX ("Attributes: " + allattrnames)

{% endraw %}
```
{: .line-numbers}

Example 2:

```adoscript
{% raw %}

# get all selected objects
CC "Modeling" GET_SELECTED
IF (objids = "") {
   CC "AdoScript" ERRORBOX "Select an instance first!"
   EXIT
}

# from the list of selected objects, extract the first objectid
SET firstselected:(token(objids,0," "))

# now get the classes of the connected instances
CC "Core" GET_CLASS_ID objid:(VAL firstselected)

# get all attributes of the selected class
CC "Core" GET_ALL_ATTRS classid:(classid)

SET allattrnames:""
FOR id in:(attrids) {
   CC "Core" GET_ATTR_NAME attrid:(VAL id)
   CC "Core" GET_ATTR_TYPE attrid:(VAL id)
   IF (LEN allattrnames > 0) {
      SET allattrnames:(allattrnames + ", ")
   }
   SET allattrnames:(allattrnames + attrname + " (" + attrtype + ")")
}

CC "AdoScript" INFOBOX ("Attributes: " + allattrnames)
CC "AdoScript" INFOBOX ("Attributes: " + allattrnames)

{% endraw %}
```
{: .line-numbers}

