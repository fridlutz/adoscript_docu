---
layout: event
category: Event
title: "DeleteApplicationModel"
tags: 1.3 1.5
---

This event is triggered after an Application model has been deleted.  

# Parameters:  

|`appmodelid (appmodid)`|intValue, contains the ID of the deleted application model.|

Exit value:



# Remarks:  



# See Also:  



Example:

The following example welcomes the user after deleting an application model.  

```adoscript
{% raw %}
	ON_EVENT "DeleteApplicationModel" {

	SETG id_AppModelId: (appmodelid)
	
	CC "AdoScript" INFOBOX "BYE BYE" 
	
  }
{% endraw %}
```
{: .line-numbers}
