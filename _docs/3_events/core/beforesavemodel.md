---
layout: event
category: Event
title: "BeforeSaveModel"
tags: 1.3 1.5
---

This event is triggered before a model is saved.  

# Parameters:  

|`modelid`|intValue, the ID of the model which is going to be saved.|
|`origin`|strValue, the origin of the save action call: "new", "save", "saveas-new" or "saveas-save".|

Exit value:

|`0`|No abortion.|
|`-1`|Abort without error.|
|`-2`|Abort with error.|
|`greater than 0`|Abort with core error code.|

# Remarks:  

It is not ensured that the model will really be saved after this event!

The parameter origin has one of these four string values:  
"new", "saveas-new" - Save has been called (automatically) directly after a new model has been created. If this happens during a saveas operation, origin has the value "saveas-new". Otherwise origin has the value "new".  
"save", "saveas-save" - Save has been called for saving a modified model. If this happens during a saveas operation, origin has the value "saveas-save". Otherwise origin has the value "save".

If the event handler is exited with a nonzero value, saving the model will not be performed. If the exit value is -1, saving is aborted without an error. If the exit value is -2, saving is aborted with an error. The difference between without and with error is that if saving has been called via the UI just in the second case an error message appears. The without error case is useful if an error message is already displayed by the event handler. If saving has been called via AdoScript, the difference is that different core error codes are returned at the delete command.  

# See Also:  



Example:  

```adoscript
{% raw %}
	ON_EVENT "BeforeSaveModel" {
	
	#do something
	
	}
{% endraw %}
```
{: .line-numbers}

