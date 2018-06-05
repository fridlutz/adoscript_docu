---
layout: event
category: Event
title: "DeleteModel"
tags: 1.3 1.5
---

This event is triggered after a model was deleted.  

# Parameters:  

|`modelid`|intValue, contains the ID of the concerned model.|

Exit value:



# Remarks:  



# See Also:  



Example:  

The following example displays an INFOBOX after deleting a model.  
```adoscript
{% raw %}
	
	ON_EVENT "DeleteModel" {

	SETG id_ModelId: (modelid)
	
	CC "AdoScript" INFOBOX "BYE BYE"
	}
	
{% endraw %}
```
{: .line-numbers}
