---
layout: commandcall
category: CommandCall
title: "SET_ATTR_VAL"
tags: 1.3 1.5
---

SET_ATTR_VAL sets an attribute value of one instance.

# Syntax:  

```adoscript
{% raw %}
CC "Core" SET_ATTR_VAL objid:id AttrSpec val:anyValue [ as-string ] .



AttrSpec :	attrid:id | attrname:strValue .
{% endraw %}
```
{: .line-numbers}

```adoscript
{% raw %}
#-->RESULT ecode:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`objid`|id AttrSpec|
|`val`|anyValue|
|`as-string`|modifier|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|

# Remarks:

The instance (library, class, connector class, model, modeling object, connector, record row or attribute profile) is specified by ID with objid. The attribute is specified by ID with attrid or by name with attrname. The new attribute value is passed with val.

When as-string is specified val must be a string which is conveted to the attribute type (e.g. INTEGER) internally. Otherwise the type of val must match the type of the attribute.

After changing a value of an attribute profile CC "Core" SAVE_LIBRARY has to be called to save that change into the database.

Note: When setting model attributes for a model that is not loaded, no error will be returned and the value of the model attribute will not be changed.

# See Also:  



Example 1:

```adoscript
{% raw %}

# get all selected objects
CC "Modeling" GET_SELECTED
IF (objids = "") {
    CC "AdoScript" ERRORBOX "No object has been selected!"
    EXIT
}

# from the list of selected objects, extract the first objectid
SET selected:(VAL token(objids,0," "))

# get the class of the selected object
CC "Core" GET_CLASS_ID objid:(selected)

# get the attribute "Name" of the class
CC "Core" GET_ATTR_ID classid:(classid) attrname:"Name"
IF (ecode) {
    CC "AdoScript" ERRORBOX "The selected object does not contain an attribute called \"Name\"!"
    EXIT
}

# set the name of the selected object
CC "Core" SET_ATTR_VAL objid:(selected) attrid:(attrid) val:"Seppl"
IF (ecode) {
    CC "AdoScript" ERRORBOX "Could not set the attribute value!"
    EXIT
}

{% endraw %}
```
{: .line-numbers}

Example 2:

```adoscript
{% raw %}

# get the current model
CC "Core" GET_ACT_MODEL
IF (modelid = "") {
    CC "AdoScript" ERRORBOX "Open a bp model first!"
    EXIT
}

# get the modelattribute "Name" of the class
CC "Core" GET_ATTR_ID classid:bp-model attrname:"Beschreibung"
IF (ecode) {
    CC "AdoScript" ERRORBOX "Model doe not contain an attribute called  \"Beschreibung\"!"
    EXIT
}

# set the model attribute
CC "Core" SET_ATTR_VAL
    objid:(VAL modelid) attrid:(attrid) val:"Modeldescription here!"
IF (ecode) {
    CC "AdoScript" ERRORBOX "Could not set the attribute value!"
    EXIT
}

{% endraw %}
```
{: .line-numbers}

Example 3:

```adoscript
{% raw %}

# get the class of the selected object
CC "Core" GET_CLASS_ID classname:"__LibraryMetaData__" bp-library

# get the attribute "Name" of the class
CC "Core" GET_ATTR_ID classid:(classid) attrname:"Grafiken erzeugen"
IF (ecode) {
    CC "AdoScript" ERRORBOX "The selected object does not contain an attribute called \"Name\"!"
    EXIT
}

# set the name of the selected object
CC "Core" SET_ATTR_VAL objid:(classid) attrid:(attrid) val:1
IF (ecode) {
    CC "AdoScript" ERRORBOX "Could not set the attribute value!"
    EXIT
}

{% endraw %}
```
{: .line-numbers}

