---
layout: event
category: Event
title: "RenameMGroup"
tags: 1.3 1.5
---

This event is triggered after a model group has been renamed.  

# Parameters:  

|`mgroupid`|intValue, the ID of the renamed model group.|
|`mgroupname`|strValue, the new name of the renamed model group.|

Exit value:



# Remarks:  



# See Also:  



Example:

The following example informs the user about the renaming of an instance.  

```adoscript
{% raw %}
	ON_EVENT "RenameMGroup" {

	SETG id_MGroupId: (mgroupid)
	SETG str_MGroupName: (mgroupname)
	
	CC "AdoScript" INFOBOX ("ModelId:  " + STR(idModelId) 
	+ "  ModelGroupName:  " + (str_MGroupName)) title: "You are renaming the model group..."
	
	}
{% endraw %}
```
{: .line-numbers}
