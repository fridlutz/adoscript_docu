---
layout: event
category: Event
title: "AfterAutoConnect"
tags: 1.3 1.5
---

This event is triggered by the model editor after auto-connectors have been created or deleted.  

# Parameters:  

|`modelid`|intValue, the ID of the concerned model.|

Exit value:



# Remarks:  

The event is triggered once for a complete action (like moving or deleting multiple objects), not for each single created or deleted auto-connector.  

# See Also:  



Example:  

```adoscript
{% raw %}
	ON_EVENT "AfterAutoConnect" {
	
	#do something
	
	}
{% endraw %}
```
{: .line-numbers}

