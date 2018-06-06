---
layout: event
category: Event
title: "DiscardInstance"
tags: 1.3 1.5
---

This event is triggered after an "instance" (see below) has been discarded.  

# Parameters:  

|`instid`|intValue, ID of the discarded instance.|
|`classid`|intValue, class ID of the discarded instance.|
|`name`|strValue, name of the discarded instance.|
|`modelid`|intValue, model ID of the discarded instance.|
|`realinstanceid`|intValue, "Real" ID of the instance (core internal ID).|
|`realclassid`|intValue, "Real" ID of the class (core internal ID).|

Exit value:



# Remarks:  

Instances are modeling objects, record rows, attribute profiles.

Note that, as the instance does not exist any more, you cannot use instid for core access here.

Mind the difference between deleting and discarding. Discarding means removing from memory, but the discarded instance may still exist as a part of its model (in the database). Deleting means, that the instance is removed from its model. Deleting implies discarding.  

# See Also:  



Example:  

The following example displays information of the instance which is going to be discarded.  

```adoscript
{% raw %}
	ON_EVENT "DiscardInstance" {
	
	SETG id_InstId: (instid) 
	SETG id_ClassId: (classid) 
	SETG id_ModelId: (modelid)
	SETG str_InstanceName: (name)
	SETG id_RealInstId: (realinstanceid)
	SETg id_RealClassId: (realclassid)
	
	CC "AdoScript" INFOBOX ("Modelid:   " + STR(id_ModelId)  + "  ClassId:  " + STR(id_ClassId) + 
	"  InstanceId:   " + STR(id_InstId) + "  InstanceName:   " + (str_InstanceName)
	+ "  RealClassId:  " + STR(id_RealClassId) + "  RealInstId:  " + STR(id_RealInstId))
	title:"You are discarding the instance..."
	}
{% endraw %}
```
{: .line-numbers}

