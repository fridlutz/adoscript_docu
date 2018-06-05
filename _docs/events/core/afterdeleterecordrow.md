---
layout: event
category: Event
title: "AfterDeleteRecordRow"
tags: 1.3 1.5
---

This event is triggered after a record row has been deleted.  

# Parameters:  

|`modelid`|intValue, ID of the changed model.|
|`instid`|intValue, ID of the changed instance (owner of the record).|
|`attrid`|intValue, ID of the RECORD attribute.|
|`pos`|intValue, Position of the new row (1 = first).|

Exit value:



# Remarks:  



# See Also:  



Example:  

The following example displays the predefined parameters after deleting a record row.  

```adoscript
{% raw %}
	ON_EVENT "AfterDeleteRecordRow" {
	SET id_ModelId: (modelid)
	SET id_InstId: (instid) 
	SET id_AttrId: (attrid)  
	SET int_PosInt: (pos) 
	SET id_RowId: (rowid)

	CC "AdoScript"  LISTBOX entries: ("Modelid   " + STR(id_ModelId)  + "$InstanceId   " + STR(id_InstId) + 
	"$AttributeId  " + STR(id_AttrId) + "$Position  " + STR(int_PosInt))  
	toksep: "$"
	}
{% endraw %}
```
{: .line-numbers}
