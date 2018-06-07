---
layout: event
category: Event
title: "ActivateModelWindow"
tags: 1.3 1.5
---

This event is triggered when a model window has been activated.  

# Parameters:  

|`modelid`|intValue, the model ID of the activated model window.|

Exit value:



# Remarks:  

If the active model window is switched from one to another, at first the DeactivateModelWindow event is triggered for the first model window, then the ActivateModelWindow event for the second

This event should not be used for action updating - use "UpdateActions" instead.

Do not show any dialog window within this event handler - that would confuse the operating system and produce an infinite recursion.  

# See Also:  

[DeactivateModelWindow](deactivatemodelwindow.html "DeactivateModelWindow")  
[UpdateActions](updateactions.html "UpdateActions")  


Example:  

```adoscript
{% raw %}
  ON_EVENT "ActivateModelWindow" {
  
  CC "AdoScript" INFOBOX ("ModelId:   " + STR(modelid))
  
 }
{% endraw %}
```
{: .line-numbers}
