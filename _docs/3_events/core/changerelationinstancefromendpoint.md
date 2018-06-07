---
layout: event
category: Event
title: "ChangeRelationInstanceFromEndpoint"
tags: 1.3 1.5
---

This event is triggered when the from instance of an relation was changed.  

# Parameters:  

|`componentid`|intValue, contains the ID of the concerned component (model, library, ...)|
|`relationinstanceid`|intValue, contains the ID of the concerned relation.|
|`oldfrominstanceid`|intValue, contains the ID of the original from-instance of the concerned relation.|
|`newfrominstanceid`|intValue, contains the ID of the new from-instance of the concerned relation.|

Exit value:



# Remarks:  



# See Also:  



Example:  

The following example displays information about the predefined parameters from the event  
"ChangeRelationInstanceFromEndpoint" in three steps.  

```adoscript
{% raw %}
  ON_EVENT "ChangeRelationInstanceFromEndpoint" {

	SETG id_ComponentId: (componentid)
	SETG id_RelationInstId: (relationinstanceid)
	SETG id_OldfromInstId: (oldfrominstanceid)
	SETG id_NewfromInstId: (newfrominstanceid)
	
	CC "AdoScript" INFOBOX ("ComponntId:   " + STR(id_ComponentId)  + 
	"  RelationInstanceId:  " + STR(id_RelationInstId)) 
	title:"You are changing the source instance of the relation instance..."
	
	CC "AdoScript" INFOBOX ("OldFromInstanceId:   " + STR(id_OldfromInstId)) title: "from..."
	CC "AdoScript" INFOBOX ("NewFromInstanceId:   " + STR(id_NewfromInstId)) title: "to..."
	}
{% endraw %}
```
{: .line-numbers}
