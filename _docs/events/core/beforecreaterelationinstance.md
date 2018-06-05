---
layout: event
category: Event
title: "BeforeCreateRelationInstance"
tags: 1.3 1.5
---

This event is triggered before a relation instance is created.  

# Parameters:  

|`frominstid`|intValue, the ID of the first ("from") instance.|
|`toinstid`|intValue, ID of the second ("to") instance.|
|`relationclassid`|intValue, ID of the relation class.|
|`componentid`|intValue, ID of the concerned component (model, library, ...)|

Exit value:

|`0`|No abortion.|
|`-1`|Abort without error.|
|`-2`|Abort with error.|
|`greater than 0`|Abort with core error code.|

# Remarks:  

This event is useful, if creating a relation instance shall be forbidden under certain circumstances.

Note that using the automatic cardinality check is the preferable solution in most cases. Automatic cardinality checking is customized through the "Cardinalities" class attributes and the "Default settings" library attribute.  

# See Also:  



Example:

The following event handler makes it impossible to draw a connector between two objects which both have the same name  
```adoscript
{% raw %}

ON_EVENT "BeforeCreateRelationInstance" {
    CC "Core" GET_OBJ_NAME objid:(frominstid)
    SET objname1:(objname)
    CC "Core" GET_OBJ_NAME objid:(toinstid)
    SET objname2:(objname)
    IF (objname1 = objname2) {
        EXIT -1
    }
}

{% endraw %}
```
{: .line-numbers}
Note that renaming objects after relation instance creation has no effect here.

