---
layout: event
category: Event
title: "CreateInstance"
tags: 1.3 1.5
---

This event is triggered after an instance was created.  

# Parameters:  

|`modelid`|intValue, contains the ID of the concerned model.|
|`classid`|intValue, contains the ID of the class.|
|`realclassid`|intValue, contains the ID of the class (core internal ID).|
|`instid`|intValue, contains the ID of the instance. (instanceid holds the same value, but is deprecated.)|
|`realinstanceid`|intValue, contains the ID of the instance (core internal ID).|

Exit value:



# Remarks:  



# See Also:  



Example:

The following example displays information of the instance which is going to be created.  

```adoscript
{% raw %}
	ON_EVENT "CreateInstance" {
	SETG id_InstId: (instid) 
	SETG id_ClassId: (classid) 
	SETG id_ModelId: (modelid)
	SETG id_RealClassId: (realclassid)
	SETG id_RealInstId: (realinstanceid)
	CC "AdoScript" INFOBOX ("Modelid:   " + STR(id_ModelId)  + "  ClassId:  " + STR(id_ClassId) + 
	"  InstanceId:   " + STR(id_InstId) + "  RealInstanceId:   " + STR(id_RealInstId) + 
	"  RealClassId:   " + STR(id_RealClassId))
	title:"You are deleting the instance..."
	}
{% endraw %}
```
{: .line-numbers}

