---
layout: event
category: Event
title: "CreateModelRef"
tags: 1.3 1.5
---

This event is triggered after a model (thread) has been added to a model group,  
i.e. a model reference from a model group to a model thread has been created.  

# Parameters:  

|`mgroupid`|intValue, ID of the model group.|
|`threadid`|intValue, ID of the model thread.|
|`modelrefid`|intValue, ID of the reference going from the model group to the model thread.|

Exit value:



# Remarks:  



# See Also:  



Example:  

The following example displays an INFOBOX with information about the created model.  

```adoscript
{% raw %}
	ON_EVENT "CreateModelRef" {
  
	SETG id_MGroupId: (mgroupid)
	SETG id_ThreadId: (threadid)
	SETG id_MRefId: (modelrefid)
	CC "AdoScript" INFOBOX ("ModelGroupId:   " + STR(id_MGroupId)  + 
	"  ThreadId:  " + STR(id_ThreadId) + 
	"  ModelReferenceId:   " + (id_MRefId))
	}
{% endraw %}
```
{: .line-numbers}
