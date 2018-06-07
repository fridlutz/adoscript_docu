---
layout: event
category: Event
title: "ChangeRelationInstanceToEndpoint"
tags: 1.3 1.5
---

This event is triggered when the to instance of an relation was changed.  

# Parameters:  

|`componentid`|intValue, contains the ID of the concerned component (model, library, ...)|
|`relationinstanceid`|intValue, contains the ID of the concerned relation.|
|`oldtoinstanceid`|intValue, contains the ID of the original to-instance of the concerned relation.|
|`newtoinstanceid`|intValue, contains the ID of the new to-instance of the concerned relation.|

Exit value:



# Remarks:  



# See Also:  



Example:  
The following example displays information about the predefined parameters from the event  
"ChangeRelationInstanceToEndpoint" in three steps.  

```adoscript
{% raw %}
  ON_EVENT "ChangeRelationInstanceToEndpoint" {

	SETG id_ComponentId: (componentid)
	SETG id_RelationInstId: (relationinstanceid)
	SETG id_OldtoInstId: (oldtoinstanceid)
	SETG id_NewtoInstId: (newtoinstanceid)
	
	CC "AdoScript" INFOBOX ("ComponntId:   " + STR(id_ComponentId)  + 
	"  RelationInstanceId:  " + STR(id_RelationInstId)) 
	title:"You are changing the target instance of the relation instance..."
	
	CC "AdoScript" INFOBOX ("OldToInstanceId:   " + STR(id_OldToInstId)) title: "from..."
	CC "AdoScript" INFOBOX ("NewToInstanceId:   " + STR(id_NewToInstId)) title: "to..."
	}
{% endraw %}
```
{: .line-numbers}
