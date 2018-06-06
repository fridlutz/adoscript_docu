---
layout: event
category: Event
title: "DiscardRelationInstance"
tags: 1.3 1.5
---

This event is triggered after a relation instance has been discarded.  

# Parameters:  

|`relninstid`|intValue, ID of the discarded relation instance.|
|`componentid`|intValue, ID of the concerned component (model, library, ...).|

Exit value:



# Remarks:  

Note that, as the relation instance does not exist any more, you cannot use relninstid for core access here.

Mind the difference between deleting and discarding. Discarding means removing from memory, but the discarded instance may still exist as a part of its model (in the database). Deleting means, that the instance is removed from its model. Deleting implies discarding.  

# See Also:  



Example

Display the relation information after discarding the relation instance!  

```adoscript
{% raw %}
	ON_EVENT "DiscardRelationInstance" {
	SET id_ComponentId: (componentid)
	SET id_RelationInstanceId: (relninstid)
	
	CC "AdoScript" INFOBOX ("Componentid:   " + STR(id_ComponentId)  + 
	"  RelationInstanceId:  " + STR(id_RelationInstanceId))  
	title:"You are discarding the relation instance..."
  }
{% endraw %}
```
{: .line-numbers}
