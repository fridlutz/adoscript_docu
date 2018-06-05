---
layout: event
category: Event
title: "DeactivateModelWindow"
tags: 1.3 1.5
---

This event is triggered when a model window has been deactivated.

# Parameters:  

|`modelid`|intValue, model ID of the deactivated model window.|

Exit value:



# Remarks:  



# See Also:  



Example :  
```adoscript
{% raw %}
  
	ON_EVENT "BeforeBuildGrModel" {
	
	SET id_ModelId: (modelid)
	
	CC "AdoScript" INFOBOX ("You are deactivating the model:  " + STR(id_ModelId))
	
	}
{% endraw %}
```
{: .line-numbers}
