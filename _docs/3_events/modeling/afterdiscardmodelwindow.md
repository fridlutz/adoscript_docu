---
layout: event
category: Event
title: "AfterDiscardModelWindow"
tags: 1.3 1.5
---

This event is triggered after a model window of the modeling editor has been closed.  

# Parameters:  

|`modelid`|intValue, contains the ID of the concerned model.|

Exit value:



# Remarks:  



# See Also:  



Example:  

```adoscript
{% raw %}
  
	ON_EVENT "AfterDiscardModelWindow" {
	
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

