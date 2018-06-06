---
layout: commandcall
category: CommandCall
title: "GET_ALL_OBJS_WITH_ATTR_VAL"
tags: 1.3 1.5
---

The command GET_ALL_OBJS_WITH_ATTR_VAL retrieves all instances (not relations!) which have a certain attribute value.

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_ALL_OBJS_WITH_ATTR_VAL modelid:id classid:id attrid:id val:str


#-->RESULT ecode:intValue objids:list
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|id, the parameter modelid specifies the model from which we want the instances.|
|`classid`|id, the parameter classid specified the lookup class.|
|`attrid`|id, the parameter attrid specifies the attribute we want to check.|
|`val`|str, the parameter val specifies the search value.|

# Returns:  

|`ecode`|intValue, the result value ecode returns an errorcode. 0 means no error.|
|`objids`|list, the result value objids returns a space-separated list of all objs which match the parameters.|

# Remarks:



# See Also:  



Example 1:

```adoscript
{% raw %}

# get current model
SEND "GET_ACTIVE_MODEL" to:"Modeling" answer:modelid
SET mid:(VAL modelid)

CC "Core" GET_CLASS_ID classname:"Aktivität"
SET cid:(classid)

CC "Core" GET_ATTR_ID classid:(cid) attrname:"Bearbeiter"
SET aid:(attrid)

CC "Core" GET_ALL_OBJS_WITH_ATTR_VAL modelid:(mid) classid:(cid) attrid:(aid) val:"{\"Bearbeiter-2\" : \"Bearbeiter\"}"

CC "AdoScript" INFOBOX ("Found " + STR tokcnt (objids, " ") + " obj(s)")

{% endraw %}
```
{: .line-numbers}
- get active model's id  
- determine ID of class 'Aktivität'  
- determine ID of attribute 'Bearbeiter'  
- query all objs  
- show number of found objects  
