---
layout: event
category: Event
title: "RenameModelThread"
tags: 1.3 1.5
---

This event is triggered when a model (thread) has been renamed.  

# Parameters:  

|`modelthreadid`|intValue, Thread ID of the renamed model.|
|`oldname`|strValue, Old model name.|
|`newname`|strValue, New model name.|
|`external`|intValue; 0 if model thread has been renamed by the current user or 1 if the model thread's name changed when refreshing the model list (model has been renamed by another user)|

Exit value:



# Remarks:  

This event does not necessarily mean that the current user changed the model thread's name.

Also if a name changes when refreshing the model list this event is triggered.  

The event on renaming a model's version number is "SetModelVersion". This only applies where versioning is enabled. However, model threads also exist without versioning being enabled, so "RenameModelThread" is also triggered for "simple", non-versioned models.

# See Also:



Example:

The following example informs the user about the renaming of an instance.  

```adoscript
{% raw %}
	ON_EVENT "RenameModelThread" {

	SETG id_ModelThreadId: (modelthreadid)
	SETG str_OldName: (oldname)
	SETG str_NewName: (newname)
	
	CC "AdoScript" INFOBOX ("ModelThreadId:  " + STR(id_ModelThreadId)) title: "You are renaming the ModelThread..."
	CC "AdoScript" INFOBOX ("OldName:  " + (str_OldName))  title: "from"
	CC "AdoScript" INFOBOX ("NewName:  " + (str_NewName))  title: "to"
	
	}
{% endraw %}
```
{: .line-numbers}
