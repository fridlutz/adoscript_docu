---
layout: event
category: Event
title: "DeleteModelThread"
tags: 1.3 1.5
---

This event is triggered after a model thread was deleted.  

# Parameters:  

|`threadid`|intValue, contains the ID of the concerned model thread.|

Exit value:



# Remarks:  



# See Also:  



Example:  

```adoscript
{% raw %}
 ON_EVENT "DeleteModelThread" {
 SET id_ThreadId: (threadid)
 CC "AdoScript" INFOBOX ("ThreadID:   " + STR(id_ThreadId)
 }
{% endraw %}
```
{: .line-numbers}
