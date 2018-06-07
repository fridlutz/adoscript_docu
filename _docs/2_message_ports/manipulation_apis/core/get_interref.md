---
layout: commandcall
category: CommandCall
title: "GET_INTERREF"
tags: 1.3 1.5
---

GET_INTERREF returns information about one reference of an INTERREF attribute value.


# Syntax:  

```adoscript
{% raw %}
CC "Core"	
GET_INTERREF	objid:id AttrSpec index:intValue .

{% endraw %}
```
{: .line-numbers}

```adoscript
{% raw %}
AttrSpec :	attrid:id | attrname:strValue .

{% endraw %}
```
{: .line-numbers}

```adoscript
{% raw %}
#-->RESULT ecode:intValue Ref
{% endraw %}
```
{: .line-numbers}

```adoscript
{% raw %}
Ref :  	ModelRef | ObjRef .

{% endraw %}
```
{: .line-numbers}

```adoscript
{% raw %}
ModelRef : 	type:"modelreference"
tmodeltype:strValue tmodelname:strValue
tmodelver:strValuetmodelid:intValue .

{% endraw %}
```
{: .line-numbers}
ObjRef : 	type:"objectreference"  
tmodeltype:strValue tmodelname:strValue  
tmodelver:strValuetmodelid:intValue  
tclassname:strValue tclassid:intValue  
tobjname:strValue tobjid:intValue .



# Parameters:  

|`objid`|id|
|`attrid`|id|
|`attrname`|strValue|
|`index`|intValue|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`type`|"modelreference"|
|`tmodeltype`|strValue|
|`tmodelname`|strValue|
|`tmodelver`|strValue|
|`tmodelid`|intValue|
|`type`|"objectreference"|
|`tmodeltype`|strValue|
|`tmodelname`|strValue|
|`tmodelver`|strValue|
|`tmodelid`|intValue|
|`tclassname`|strValue|
|`tclassid`|intValue|
|`tobjname`|strValue|
|`tobjid`|intValue|

# Remarks:

Use GET_INTERREF_COUNT to get the number of references (count).  
The argument attrid has to be set to the ID of the attribue. Alternatively the name of an attribute can be specified with attrname. The argument objid has to be set to the ID of the instance.  
The accessed reference index has to be passed in the argument index, where 0 means first reference, count-1 last reference.

The return variable tmodeltype is set to the modeltype of the referenced model, tmodelname is set to the name of the referenced model and tmodelver is set to the version of the referenced model.

If the reference is a modelreference, type is set to the string "modelreference". tmodelid contains the ID of the referenced model version. If the reference is invalid the value is -1.

If the reference is an objectreference, type is set to the string "objectreference", tclassname is set to the name of the class of the target object and tobjname is set to the name of the target object.tmodelid contains the ID of the referenced model version. tclassid contains the ID of the referenced class. tobjid contains the ID of the referenced object, but only if the target model is loaded - else tobjid is -1. If the reference is invalid the values of tmodelid, tclassid and tobjid are -1.


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
# get all attributes
CC "Core" GET_ALL_ATTRS classid:(classid)
# for each attribute, check if it is an interref attribute
SET result:"Interref attributes:\n\n"
FOR attrid in:(attrids) {
   CC "Core" GET_ATTR_TYPE attrid:(VAL attrid)
   CC "Core" GET_ATTR_NAME attrid:(VAL attrid)
   IF (attrtype = "INTERREF") {
      # for each interref attribute, get all interrefs
      CC "Core" GET_INTERREF_COUNT objid:(selected) attrid:(VAL attrid)
      SET result:(result+attrname+" has # references: "+STR count+"\n")
   }
}
# display the result
CC "AdoScript" INFOBOX (result)

{% endraw %}
```
{: .line-numbers}

