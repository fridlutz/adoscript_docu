---
layout: event
category: Event
title: "CreateMGroup"
tags: 1.3 1.5
---

This event is triggered after a model group has been created.  

# Parameters:  

|`mgroupid`|intValue, ID of the created model group.|
|`supermgroupid`|intValue, ID of the new group's parent.|
|`mgroupname`|STRValue, Name of the created model group.|

Exit value:



# Remarks:  



# See Also:  

Example:  
```adoscript
{% raw %}
  ON_EVENT "CreateMGroup" {
  
  SETG id_MGroupId: (mgroupid)
  SETG id_SuperMGroupId: (supermgroupid)
  SETG id_MGroupname: (mgroupname)
  CC "AdoScript" INFOBOX ("ModelGroupId:   " + STR(id_MGroupId)  + 
  "  SuperModelGroupId:  " + STR(id_SuperMGroupId) + 
  "  ModelGroupName:   " + (id_MGroupname))
  }
{% endraw %}
```
{: .line-numbers}
