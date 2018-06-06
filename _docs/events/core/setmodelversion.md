---
layout: event
category: Event
title: "SetModelVersion"
tags: 1.3 1.5
---

This event is triggered when the version number of a model has been renamed.  

# Parameters:  

|`modelversionid`|intValue, version ID of the renamed model.|
|`oldver`|strValue, old version number.|
|`newver`|strValue, new ersion number.|

Exit value:



# Remarks:  

This event only applies where versioning is enabled. Without versioning, the version number is part of the model name (model thread name), so "RenameModelThread" is triggered when changing the version number of a non-versioned model.  

# See Also:  

[RenameModelThread](renamemodelthread.html "RenameModelThread")  


Example:  
```adoscript
{% raw %}
	ON_EVENT "SetModelVersion" {

	SETG id_ModelVersionId: (modelversionid)
	SETG str_OldVersion: (oldver)
	SETG str_NewVersion: (newver)
	
	CC "AdoScript" INFOBOX ("ModelVersionId:  " + STR(id_ModelVersionId)) title: "You are renaming the ModelVersion..."
	CC "AdoScript" INFOBOX ("OldName:  " + (str_OldName))  title: "from"
	CC "AdoScript" INFOBOX ("NewName:  " + (str_NewName))  title: "to"
	
	}
{% endraw %}
```
{: .line-numbers}
