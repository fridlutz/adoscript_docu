---
layout: event
category: Event
title: "DeleteAPVersion"
tags: 1.3 1.5
---

This event is triggered after an attribute profile version has been deleted.  

# Parameters:  

|`apversionid`|intValue, ID of the deleted attribute profile.|
|`apclassid`|intValue, class ID of the deleted attribute profile.|
|`name`|strValue, name of the deleted attribute profile.|

Exit value:



# Remarks:  



# See Also:  



Example:  

```adoscript
{% raw %}
	ON_EVENT "DeleteAPVersion" {
	
	#do something
	
	}
{% endraw %}
```
{: .line-numbers}

