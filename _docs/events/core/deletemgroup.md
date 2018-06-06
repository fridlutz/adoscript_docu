---
layout: event
category: Event
title: "DeleteMGroup"
tags: 1.3 1.5
---

This event is triggered after a model group has been deleted.  

# Parameters:  

|`mgroupid`|intValue, the ID of the deleted model group.|

Exit value:



# Remarks:  



# See Also:  



Example:

```adoscript
{% raw %}
  ON_EVENT "DeleteMGroup" {
  
  SETG id_MGroupId: (mgroupid)
  CC "AdoScript" INFOBOX ("ModelGroupId:   " + STR(id_MGroupId)) title: "BYE BYE"
  }
{% endraw %}
```
{: .line-numbers}

