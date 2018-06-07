---
layout: event
category: Event
title: "RenameInstance"
tags: 1.3 1.5
---

This event is triggered when an "instance" (see below) has been renamed.  

# Parameters:  

|`instid`|intValue, the ID of the renamed instance.|
|`oldname`|strValue, the old instance name.|
|`newname`|strValue, the new instance name.|

Exit value:



# Remarks:  

Instances are modeling objects, record rows, attribute profiles.  

# See Also:  



Example:  

The following example informs the user about the renaming of an instance.  

```adoscript
{% raw %}
	ON_EVENT "RenameInstance" {

	SETG id_InstId: (instid)
	SETG str_OldName: (oldname)
	SETG str_NewName: (newname)
	
	CC "AdoScript" INFOBOX ("InstanceId:  " + STR(id_InstId)) title: "You are renaming the model..."
	CC "AdoScript" INFOBOX ("OldName:  " + (str_OldName))  title: "from"
	CC "AdoScript" INFOBOX ("NewName:  " + (str_NewName))  title: "to"
	
	}
{% endraw %}
```
{: .line-numbers}

