---
layout: event
category: Event
title: "RenameAttrProf"
tags: 1.3 1.5
---

This event is triggered when an attribute profile has been renamed.  

# Parameters:  

|`apthreadid`|intValue, the ID of the attribute profile thread|
|`oldname`|strValue, the old name of the attribute profile thread.|
|`newname`|strValue, the new name of the attribute profile thread.|

Exit value:



# Remarks:  



# See Also:  



Example:

The following example informs the user about the renaming of an attribute profile.  

```adoscript
{% raw %}
	ON_EVENT "RenameAttrProf" {

	SETG id_APThreadlId: (appmodelid)
	SETG str_APOldName: (oldname)
	SETG str_APNewName: (newname)
	
	CC "AdoScript" INFOBOX ("AttributeProfileThreadId:  " + STR(id_APThreadlId)) 
	title: "You are renaming the model..."
	CC "AdoScript" INFOBOX ("OldName:  " + (str_APOldName))  title: "from"
	CC "AdoScript" INFOBOX ("NewName:  " + (str_APNewName))  title: "to"
	
	}
{% endraw %}
```
{: .line-numbers}
