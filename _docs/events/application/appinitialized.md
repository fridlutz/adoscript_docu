---
layout: event
category: Event
title: "AppInitialized"
tags: 1.3 1.5
---

This event is triggered after the initialization of the application is finished.  

# Parameters:  

none

Exit value:



# Remarks:  

Note that this event is not always the first one which is triggered at application startup. This means that in events like "SetAttributeValue" global variables which are initialized in "AppInitialized" should never be accessed without checking existence.  

# See Also:  



Example 1:

```adoscript
{% raw %}

ON_EVENT "AppInitialized"�{
    �  CC "AdoScript" INFOBOX "The initialization is finished."
  �}

{% endraw %}
```
{: .line-numbers}
lets a message appear after the initialization of the application is finished.

