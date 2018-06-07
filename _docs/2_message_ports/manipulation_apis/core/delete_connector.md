---
layout: commandcall
category: CommandCall
title: "DELETE_CONNECTOR"
tags: 1.3 1.5
---

DELETE_CONNECTOR deletes a single connector.

# Syntax:  

```adoscript
{% raw %}
CC "Core" DELETE_CONNECTOR ConnectorID | FromToIDs .

{% endraw %}
```
{: .line-numbers}

```adoscript
{% raw %}
ConnectorID :	modelid:intValue objid:intValue .
{% endraw %}
```
{: .line-numbers}

```adoscript
{% raw %}
FromToIDs :	modelid:intValue fromobjid:intValue fromobjid:intValue classid:intValue .

{% endraw %}
```
{: .line-numbers}

```adoscript
{% raw %}
#-->RESULT ecode:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|intValue, the ID of the model containing the connector to be deleted.|
|`objid`|intValue, the instance ID of the connector to be deleted.|
|`fromobjid`|intValue, the IDs of the source object of the connector to be deleted|
|`fromobjid`|intValue, the IDs of the target object of the connector to be deleted|
|`classid`|intValue, the relation class ID of the connector.|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|

# Remarks:

Two forms are provided : Passing a connector ID or passing the IDs of the related objects together with the connector's relation class ID.

# See Also:  



Example 1:

```adoscript
{% raw %}

SEND "GET_ACTIVE_MODEL" to:"Modeling" answer:modelid
SET mid:(VAL modelid)

CC "Core" GET_CLASS_ID classname:"Aktivität"
SET cid:(classid)

CC "Core" GET_CLASS_ID classname:"Nachfolger" relation
SET rcid:(classid)

CC "Core" GET_OBJ_ID modelid:(mid) classid:(cid) objname:"Aktivität-1"
SET iid1:(objid)

CC "Core" GET_OBJ_ID modelid:(mid) classid:(cid) objname:"Aktivität-2"
SET iid2:(objid)

CC "Core" DELETE_CONNECTOR modelid:(mid) fromobjid:(iid1) toobjid:(iid2) classid:(rcid)

CC "Modeling" REBUILD_DRAWING_AREA modelid:(mid)

{% endraw %}
```
{: .line-numbers}

