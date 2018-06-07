---
layout: event
category: Event
title: "BeforeDeleteModel"
tags: 1.3 1.5
---

This event is triggered before a model is deleted.  

# Parameters:  

|`modelid`|intValue, theID of the model to be deleteded.|

Exit value:

|`0`|No abortion.|
|`-1`|Abort without error.|
|`-2`|Abort with error.|
|`greater than 0`|Abort with core error code.|

# Remarks:  

Mind the difference between deleting and discarding. Discarding means removing from memory, but the discarded model may still exist in the database. Deleting means, that the instance is removed from the databased. Deleting implies discarding.  

# See Also:  



Example:  

The following example makes it impossible to delete a model in a model group named “My Models”  

```adoscript
{% raw %}
	ON_EVENT "BeforeDeleteModel" {
	SET id_ModelId: (modelid)     
	CC "Core" GET_MODELGROUP_NAME mgroupid:(mgroupid)    
	IF (mgroupname = "My Models") {        
	SET err:"Deleting Models in this group is not allowed!"        
	CC "AdoScript" ERRORBOX (err)        EXIT -1  # abort without error    
		}
	}
{% endraw %}
```
{: .line-numbers}

