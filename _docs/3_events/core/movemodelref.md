---
layout: event
category: Event
title: "MoveModelRef"
tags: 1.3 1.5
---

This event is triggered after a model (thread) has been moved out from one model group into another model group, i.e. the from endpoint of the according model reference changed.  

# Parameters:  

|`modelrefid`|intValue, ID of the model reference.|
|`newmgroupid`|intValue, ID of the model group from which the model reference is outgoing now.|

Exit value:



# Remarks:  



# See Also:  



Example:  

```adoscript
{% raw %}
	ON_EVENT "MoveMGroup" {
	
	SETG id_MRefId: (modelrefid)  
	SETG id_NewMGroupId: (newmgroupid)
	
	CC "AdoScript" INFOBOX ("ModelRefId:   " + STR(id_MRefId)  + "  NewModelGroupId:  " + STR(id_NewMGroupId))
	}
{% endraw %}
```
{: .line-numbers}

