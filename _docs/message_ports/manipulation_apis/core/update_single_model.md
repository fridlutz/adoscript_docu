---
layout: commandcall
category: CommandCall
title: "UPDATE_SINGLE_MODEL"
tags: 1.3 1.5
---

UPDATE_SINGLE_MODEL inserts a model into the core's internal structures. It does the same as UPDATE_MODEL_LIST, but just for one model instead of for all models.

# Syntax:  

```adoscript
{% raw %}
CC "Core" UPDATE_SINGLE_MODEL modelid:id

#--> RESULT ecode:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|the ID of the model to be updated.|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|

# Remarks:

This command is useful for cache implementations, e.g. of  a webservice application. If the cache detects that a new model existst, e.g. after having called  
CC "DB" GET_ALL_DATES_OF_LAST_CHANGE,  
that model cannot be accessed while the core's internal structures are not up-to-date, Updating with UPDATE_SINGLE_MODEL is much faster than UPDATE_MODEL_LIST.

# See Also:  

[UPDATE_MODEL_LIST](update_model_list.html "UPDATE_MODEL_LIST")  


Example 1:

```adoscript
{% raw %}

SET result:""
CC "DB" GET_ALL_DATES_OF_LAST_CHANGE
FOR pair in:(dates) sep:"\n" {
    SET modelid:(VAL token(pair, 0, "\t"))
    CC "Core" GET_MODEL_MODELTYPE modelid:(modelid)
    IF (ecode) {
        CC "Core" UPDATE_SINGLE_MODEL modelid:(modelid)
        CC "Core" debug GET_MODEL_INFO modelid:(modelid)
        SET result:(result + "New model: " + modelname + "\n")
    } ELSE {
        CC "Core" GET_MODEL_INFO modelid:(modelid)
        SET result:(result + "Old model: " + modelname + "\n")
    }
}
CC "AdoScript" VIEWBOX text:(result)

{% endraw %}
```
{: .line-numbers}

