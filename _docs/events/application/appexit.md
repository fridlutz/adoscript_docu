---
layout: event
category: Event
title: "AppExit"
tags: 1.3 1.5
---

This event is triggered before the application is going to shutdown.  

# Parameters:  

none

# Remarks:  

This event is triggered before the application is going to shutdown.  

# See Also:  



Example:  

```adoscript
{% raw %}
	ON_EVENT "AppExit" {
	CC "AdoScript" INFOBOX "BYE BYE" title: "Shut Down"
	}
{% endraw %}
```
{: .line-numbers}
