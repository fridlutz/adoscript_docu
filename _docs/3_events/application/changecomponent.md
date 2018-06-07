---
layout: event
category: Event
title: "ChangeComponent"
tags: 1.3 1.5
---

This event is triggered after the user has changed the ADOxx component.  

# Parameters:  

|`old`|intValue, contains the number of the old component (-1 indicates it is the first component)|
|`new`|intValue, contains the number of the new component.|

# Remarks:  



# See Also:  



Example:

```adoscript
{% raw %}
	ON_EVENT "ChangeComponent" {
	
	#do something
	
	}
{% endraw %}
```
{: .line-numbers}
