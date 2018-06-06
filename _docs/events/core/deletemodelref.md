---
layout: event
category: Event
title: "DeleteModelRef"
tags: 1.3 1.5
---

his event is triggered after a model (thread) has been removed from a model group, i.e. the model reference from that model group to the model thread has been deleted.  

# Parameters:  

|`mgroupid`|intValue, the ID of the model group.|
|`threadid`|intValue, the ID of the model thread.|
|`modelrefid`|intValue, the ID of the reference going from the model group to the model thread.|

Exit value:



# Remarks:  

Note that, as the model reference does not exist any more, you cannot use modelrefid for core access here.  

# See Also:  



Example:  

The following example displays an INFOBOX with information about the deleted model.  

```adoscript
{% raw %}
	ON_EVENT "DeleteModelRef" {
  
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
