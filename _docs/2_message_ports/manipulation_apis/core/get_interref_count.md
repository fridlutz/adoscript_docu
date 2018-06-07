---
layout: commandcall
category: CommandCall
title: "GET_INTERREF_COUNT"
tags: 1.3 1.5
---

GET_INTERREF_COUNT returns the number of references contained in an INTERREF attribute value.


# Syntax:  

```adoscript
{% raw %}
CC "Core"	
GET_INTERREF_COUNT	objid:id AttrSpec .

{% endraw %}
```
{: .line-numbers}
AttrSpec :	attrid:id | attrname:strValue .



```adoscript
{% raw %}
#-->RESULT ecode:intValue count:anyValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`objid`|id, the argument objid has to be set to the ID of the instance.|
|`attrid`|id, the argument attrid has to be set to the ID of the attribue.|
|`attrname`|strValue, alternatively the name of an attribute can be specified with attrname.|

# Returns:  

|`ecode`|intValue, contains the error code or is 0 in case of success.|
|`count`|anyValue, the return variable count is set to the number of references that are contained in the accessed attribute value.|

# Remarks:




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

