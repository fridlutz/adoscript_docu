---
layout: event
category: Event
title: "BeforeDiscardModel"
tags: 1.3 1.5
---

This event is triggered before a model is discarded.  

# Parameters:  

|`modelid `|intValue, contains the ID of the concerned model.|

Exit value:



# Remarks:  



# See Also:  



Example:  
The following example makes it impossible to discard a model in a model group named “My Models”  

```adoscript
{% raw %}
	ON_EVENT "BeforeDiscardModel" {
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

