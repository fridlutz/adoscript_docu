---
layout: commandcall
category: CommandCall
title: "REMOVE_ALL_INTERREFS"
tags: 1.3 1.5
---

REMOVE_ALL_INTERREFS removes all references from an interref attribute.

# Syntax:  

```adoscript
{% raw %}
CC "Core" REMOVE_ALL_INTERREFS objid:intValue attrid:intValue Target .


#-->RESULT ecode:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`objid`|intValue, the ID of the object which is owner of the attribute has to be passed as argument objid.|
|`attrid`|intValue, the ID of the INTERREF attribute has to be passed as argument attrid.|
Target

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|

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
FOR attrid in:(attrids) {
    CC "Core" GET_ATTR_TYPE attrid:(VAL attrid)
    CC "Core" GET_ATTR_NAME attrid:(VAL attrid)
    IF (attrtype = "INTERREF") {
        # for each interref attribute, get all interrefs
        CC "Core" REMOVE_ALL_INTERREFS objid:(selected) attrid:(VAL attrid)
   }
}

# show info
CC "AdoScript" INFOBOX "All references of the selected instance have been removed!"

{% endraw %}
```
{: .line-numbers}

