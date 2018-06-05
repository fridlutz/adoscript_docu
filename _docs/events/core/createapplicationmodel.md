---
layout: event
category: Event
title: "CreateApplicationModel"
tags: 1.3 1.5
---

This event is triggered after an Applicaiton model was created.  

# Parameters:  

|`appmodelid (appmodid)`|intValue, contains the ID of the created application model.|
|`appmodelname (appmodname)`|intValue, contains the name of the created application model.|
|`onthread`|intValue, contains a bool flag (0 or 1) whether the application model was defined on threads or on versions.|

Exit value:



# Remarks:  



# See Also:  



Example:  

The following example welcomes the user after creating an application model.  

```adoscript
{% raw %}
	ON_EVENT "CreateApplicationModel" {

	SETG id_AppModelId: (appmodelid)
	SETG str_AppModelName: (appmodelname)
	SETG id_OnThread: (onthread)
	
	CC "AdoScript" INFOBOX "HELLO" 
{% endraw %}
```
{: .line-numbers}
}  
