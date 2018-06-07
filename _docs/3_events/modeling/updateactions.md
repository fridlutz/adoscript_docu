---
layout: event
category: Event
title: "UpdateActions"
tags: 1.3 1.5
---

This event is triggered when the enabling/disabling of the application's actions (menu items and quick access bar) could change. This is the case when a model window is being opened/activated/closed and when the model of the active model window is being modifyed/saved.  

# Parameters:  

|`modelid`|intValue, model ID of the active model window.|

Exit value:

none

# Remarks:  

If no model window is active (i.e. no model window is opened), modelid has the value -1.  

# See Also:



Example :  

```adoscript
{% raw %}
  
	ON_EVENT "BeforeCreateModelWindow" {
	
	SETG nNewModelID:(modelid)
	
	CC "Core" GET_ALL_OBJS modelid:(nNewModelID)
	SETL lObjIDs:(objids)
	SETL nObjsCount:(tokcnt(lObjIDs))
	
	CC "Core" GET_ALL_CONNECTORS modelid:(nNewModelID)
	SETL lConnectorIDs:(objids)
	SETL nConnectorsCount:(tokcnt(lConnectorIDs))
	
	CC "AdoScript" INFOBOX ("The model contains " + STR nObjsCount + 
	" objects and " + STR nConnectorsCount + " connectors.")
 }
{% endraw %}
```
{: .line-numbers}

