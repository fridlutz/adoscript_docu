---
layout: event
category: Event
title: "BeforeCreateModel"
tags: 1.3 1.5
---

This event is triggered before a model is created.  

# Parameters:  

|`threadid`|intValue, ID of the model thread.|
|`modelname`|strValue, model name.|
|`version`|strValue, version number.|
|`origin`|strValue; "new" : The model has been created as completely new (empty) model, "saveas-new" : The model has been created as a copy of an existing model.|

Exit value:

|`0`|No abortion.|
|`-1`|Abort without error.|
|`-2`|Abort with error.|
|`greater than 0`|Abort with core error code.|

# Remarks:  



# See Also:  



Example:  

```adoscript
{% raw %}
	ON_EVENT "BeforeCreateModel" {
	
	#do something
	
	}
{% endraw %}
```
{: .line-numbers}

