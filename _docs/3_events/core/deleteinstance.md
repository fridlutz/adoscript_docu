---
layout: event
category: Event
title: "DeleteInstance"
tags: 1.3 1.5
---

This event is triggered after an "instance" (see below) has been deleted.  

# Parameters:  

|`instid`|intValue, the ID of the deleted instance. (instanceid holds the same value, but is deprecated.)|
|`classid`|intValue, the class ID of the deleted instance.|
|`name`|strValue, the name of the deleted instance.|
|`modelid`|intValue, the model ID of the deleted instance.|

Exit value:



# Remarks:  

Instances are modeling objects, record rows, attribute profiles.

Note that, as the instance does not exist any more, you cannot use instid for core access here.

Mind the difference between deleting and discarding. Discarding means removing from memory, but the discarded instance may still exist as a part of its model (in the database). Deleting means, that the instance is removed from its model. Deleting implies discarding.  

# See Also:  



Example:  

The following example displays information of the instance which is going to be deleted.  

```adoscript
{% raw %}
	ON_EVENT "DeleteInstance" {
	
	SETG id_InstId: (instid) 
	SETG id_ClassId: (classid) 
	SETG id_ModelId: (modelid)
	SETG str_InstanceName: (name)
	
	CC "AdoScript" INFOBOX ("Modelid:   " + STR(id_ModelId)  + "  ClassId:  " + STR(id_ClassId) + 
	"  InstanceId:   " + STR(id_InstId) + "  InstanceName:   " + (str_InstanceName))
	title:"You are deleting the instance..."
	}
{% endraw %}
```
{: .line-numbers}

