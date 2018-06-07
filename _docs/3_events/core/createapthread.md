---
layout: event
category: Event
title: "CreateAPThread"
tags: 1.3 1.5
---

This event is triggered after an AttrProf thread was created.  

# Parameters:  

|`apdirid`|intValue, contains the ID of the AttrProf directory in which the thread was created.|
|`apthreadid`|intValue, contains the ID of the created thread.|
|`apthreadname`|intValue, contains the name of the created thread.|

Exit value:



# Remarks:  



# See Also:  



Example:  

```adoscript
{% raw %}
	ON_EVENT "CreateAPThread" {
	
	#do something
	
	}
{% endraw %}
```
{: .line-numbers}
