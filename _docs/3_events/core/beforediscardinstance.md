---
layout: event
category: Event
title: "BeforeDiscardInstance"
tags: 1.3 1.5
---

This event is triggered before an "instance" (see below) is discarded.  

# Parameters:  

|`instid`|intValue, the ID of the discardedd instance.|
|`classid`|intValue, the class ID of the discarded instance.|
|`modelid`|intValue, the model ID of the discarded instance.|
|`realinstanceid`|intValue, the "Real" ID of the instance (core internal ID).|
|`realclassid`|intValue, the "Real" ID of the class (core internal ID).|

Exit value:

|`0`|No abortion.|
|`-1`|Abort without error.|
|`-2`|Abort with error.|
|`greater than 0`|Abort with core error code.|

# Remarks:  

Instances are: Modeling objects, record rows, attribute profiles.

Mind the difference between deleting and discarding. Discarding means removing from memory, but the discarded instance may still exist as a part of its model (in the database). Deleting means, that the instance is removed from its model. Deleting implies discarding.

There should be no reason to abort a discard operation.  

# See Also:  



Example:  
The following example displays the predefined parameters before discarding an instance in an INFOBOX.  

```adoscript
{% raw %}
	ON_EVENT "BeforeDiscardInstance" {
	SET id_InstId: (instid) 
	SET id_ClassId: (classid) 
	SET id_ModelId: (modelid)
	SET id_RealInstId:(realinstanceid)
	SET id_RealClassId: (realclassid)
	CC "AdoScript" INFOBOX ("Modelid:   " + STR(id_ModelId)  + "  ClassId:  " + STR(id_ClassId) + 
	"  InstanceId:   " + STR(id_InstId) + "  RealClassId:  " + STR(id_RealClassId) + "  RealInstanceId:  " 
	+ STR(id_RealInstId))  title:"You are discarding the instance..."
	}
{% endraw %}
```
{: .line-numbers}

