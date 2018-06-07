---
layout: event
category: Event
title: "PrintModel"
tags: 1.3 1.5
---

This event is triggered before a model is printed.  

# Parameters:  

|`modelid`|intValue, the ID of the model to be printed.|

Exit value:



# Remarks:  



# See Also:  



Example :  
```adoscript
{% raw %}
  	
	ON_EVENT "BeforeBuildGrModel" {
	
	SET id_ModelId: (modelid)
	
	CC "AdoScript" INFOBOX ("You are printing the model:  " + STR(id_ModelId))
	
	}
{% endraw %}
```
{: .line-numbers}

