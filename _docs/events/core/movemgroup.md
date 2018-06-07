---
layout: event
category: Event
title: "MoveMGroup"
tags: 1.3 1.5
---

This event is triggered after a model group has been moved out from its original parent model group into another model group.  

# Parameters:  

|`mgroupid`|intValue, ID of the moved model group.|
|`oldsupermgroupid`|intValue, ID of the old parent.|
|`newsupermgroupid`|intValue, ID of the new parent.|

Exit value:



# Remarks:  



# See Also:



Example:

```adoscript
{% raw %}
	ON_EVENT "MoveMGroup" {
	
	SETG id_MGroupId: (mgroupid) 
	SETG id_OldSGroupId: (oldsupermgroupid) 
	SETG id_NewSGroupId: (newsupermgroupid)
	
	CC "AdoScript" INFOBOX ("GroupId:   " + STR(id_MGroupId)  + "  OldSuperMGroupId:  " + STR(id_OldSGroupId) + 
	"  NewSuperMGroupId:   " + STR(id_NewSGroupId))
	}
{% endraw %}
```
{: .line-numbers}
