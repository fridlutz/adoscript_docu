---
layout: commandcall
category: CommandCall
title: "REMOVE_INTERREF"
tags: 1.3 1.5
---

REMOVE_INTERREF removes a single reference from an interref attribute.

# Syntax:  

```adoscript
{% raw %}
CC "Core" REMOVE_INTERREF objid:intValue attrid:intValue Target index:intValue .


#-->RESULT ecode:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`objid`|intValue, the ID of the object which is owner of the attribute has to be passed as argument objid.|
|`attrid`|intValue, the ID of the INTERREF attribute has to be passed as argument attrid.|
Target
|`index`|intValue, the index of the reference to be deleted has to be passed as argument index, where index starts at 0.|

# Returns:  

|`ecode`|intValue, if an invalid index is passed ecode contains a non-zero value.|

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
        CC "Core" REMOVE_INTERREF objid:(selected) attrid:(VAL attrid) index:0
    }
}

# show info
CC "AdoScript" INFOBOX
        "All first references of the selected object have been removed!"

{% endraw %}
```
{: .line-numbers}

