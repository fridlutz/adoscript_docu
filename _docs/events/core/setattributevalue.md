---
layout: event
category: Event
title: "SetAttributeValue"
tags: 1.3 1.5
---

This event is triggered after an attribute value has been changed.  

# Parameters:  

|`instid`|intValue, ID of the changed instance.|
|`attrid`|intValue, Attribute ID.|
|`modelid`|intValue, ID of the model containing the changed instance.|
|`attrtypeid`|intValue, Attribute type code: 0 INTEGER, 1 DOUBLE, 2 STRING, 3 DISTRIBUTION, 4 TIME, 5 ENUMERATION, 6 ENUMERATIONLIST, 7 CORE_LONGSTRING, 8 PROGRAMCALL, 9 INTERREF, 10 EXPRESSION, 11 RECORD, 12 ATTRPROFREF, 13 DATE, 14 DATETIME, 15 CLOB|
|`oldval`|strValue, the original value (as string). This is the Core internal value (not UI value). For attributes of type RECORD this is always an empty string. The new value can be determined via the "Core" MessagePort.|

Exit value:



# Remarks:  



# See Also:  



Example:  

```adoscript
{% raw %}
	ON_EVENT "SetAttributeValue" {
	SETG id_ModelId:(modelid)
	SETG id_InstId:(instid)
	SETG id_AttrId:(attrid)
	SETG id_AttrTypeId:(attrtypeid) 
	SETG str_OldValue: (oldval)
	
	CC "AdoScript" INFOBOX 
	("Modelid:   " + STR(id_ModelId)  + 
	"  InstanceId:  " + STR(id_InstId) + 
	"  AttributeId:  " + STR(id_AttrId) + 
	"  AttributeTypeId:   " + STR(id_AttrTypeId) + 
	"  OldValue:   " + (str_OldValue))
	title:"You have successfully set a new attribute value..."
	
	}
{% endraw %}
```
{: .line-numbers}
