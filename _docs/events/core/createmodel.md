---
layout: event
category: Event
title: "CreateModel"
tags: 1.3 1.5
---

This event is triggered after a new model has successfully been created.  

# Parameters:  

|`modelid `|intValue, contains the ID of the concerned model.|

Exit value:



# Remarks:  



# See Also:  



Example:  
```adoscript
{% raw %}
	
	ON_EVENT "CreateModel" {

	SETG id_ModelId: (modelid)
	
	CC "AdoScript" INFOBOX "HELLO"
	}
	
{% endraw %}
```
{: .line-numbers}
