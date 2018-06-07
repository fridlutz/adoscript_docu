---
layout: event
category: Event
title: "DeleteRelationInstance"
tags: 1.3 1.5
---

This event is triggered after a relation was deleted.  

# Parameters:  

|`componentid`|intValue, contains the ID of the concerned component (model, library, ...)|
|`relationinstanceid`|intValue, contains the ID of the concerned relation.|
|`relationclassid`|intValue, contains the ID of the concerned relationclass.|
|`frominstanceid`|intValue, contains the ID of the from-instance of the concerned relation.|
|`toinstanceid`|intValue, contains the ID of the to-instance of the concerned relation.|

Exit value:



# Remarks:  



# See Also:  



Example:  

Display the relation information after deleting the relation instance!  

```adoscript
{% raw %}
	ON_EVENT "DeleteRelationInstance" {
	SET id_ComponentId: (componentid)
	SET id_RelationInstanceId: (relationinstanceid)
	SET id_RelationClassId: (relationclassid) 
	SET id_FromInstanceId: (frominstanceid) 
	SET id_ToInstanceId: (toinstanceid) 
	
	CC "AdoScript" INFOBOX ("Componentid:   " + STR(id_ComponentId)  + 
	"  RelationClassId:  " + STR(id_RelationClassId) + 
	"  RelationInstanceId:  " + STR(id_RelationInstanceId) +
	"  FromInstanceId:   " + STR(id_FromInstanceId) + 
	"  FromInstanceId:   " + STR(id_FromInstanceId))  title:"You are deleting the relation instance..."
  }
{% endraw %}
```
{: .line-numbers}

