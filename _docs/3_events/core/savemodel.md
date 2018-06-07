---
layout: event
category: Event
title: "SaveModel"
tags: 1.3 1.5
---

A model has been saved. The ID of the model is passed via modelid.  

# Parameters:  

|`modelid`|intValue, ID of the model which is going to be saved.|
|`origin`|strValue, origin of the save action call: "new", "save", "saveas-new" or "saveas-save".|

Exit value:



# Remarks:  

The parameter origin has one of these four string values  
"new", "saveas-new" - Save has been called (automatically) directly after a new model has been created. If this happens during a saveas operation, origin has the value "saveas-new". Otherwise origin has the value "new".  
"save", "saveas-save" - Save has been called for saving a modified model. If this happens during a saveas operation, origin has the value "saveas-save". Otherwise origin has the value "save".  

# See Also:  



Example:

```adoscript
{% raw %}

ON_EVENT "SaveModel" {
	
	CC "AdoScript" INFOBOX "Your Model is Safe!" 	
	}

{% endraw %}
```
{: .line-numbers}

