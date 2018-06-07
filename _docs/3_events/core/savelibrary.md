---
layout: event
category: Event
title: "SaveLibrary"
tags: 1.3 1.5
---

This event is triggered when a library is saved.  

# Parameters:  

|`libid`|intValue, the ID of the concerned library.|

Exit value:



# Remarks:  

This event is also triggered when changes on an attribute profile were done!  

# See Also:  



Example:  
```adoscript
{% raw %}
	ON_EVENT "SaveLibrary" {
	
	#do something
	
	}
{% endraw %}
```
{: .line-numbers}

