---
layout: event
category: Event
title: "RenameApplicationModel"
tags: 1.3 1.5
---

This event is triggered when an application model has been renamed.  

# Parameters:  

|`appmodelid`|intValue, ID of the renamed application model.|
|`oldname`|strVlaue, the old application model name.|
|`newname`|strVlaue, the new application model name.|

Exit value:



# Remarks:  



# See Also:  



Example:

The following example welcomes the user after renaming an application model.  

```adoscript
{% raw %}
	ON_EVENT "RenameApplicationModel" {

	SETG id_AppModelId: (appmodelid)
	SETG str_OldName: (oldname)
	SETG str_NewName: (newname)
	
	CC "AdoScript" INFOBOX ("ModelId:  " + STR(id_AppModelId)) title: "You are renaming the model..."
	CC "AdoScript" INFOBOX ("OldName:  " + (str_OldName))  title: "from"
	CC "AdoScript" INFOBOX ("NewName:  " + (str_NewName))  title: "to"
	
	}
{% endraw %}
```
{: .line-numbers}
