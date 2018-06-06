---
layout: event
category: Event
title: "AfterUpdateGrObjects"
tags: 1.3 1.5
---



# Parameters:  

|`modelid`|intValue, the model ID of the updated drawing area.|
|`objids`|array, container of IDs of updated graphical objects.|
|`repaintrect`|map, coordinates of the repaint rectangle as a (string) map with keys "x", "y", "w" and "h".|

Exit value:



# Remarks:  



# See Also:  



Example:  

```adoscript
{% raw %}
	ON_EVENT "AfterUpdateGrObjects" {
	
	#do something
	
	}
{% endraw %}
```
{: .line-numbers}

