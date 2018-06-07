---
layout: commandcall
category: CommandCall
title: "GET_ALL_MODEL_CHANGE_COUNT_VALUES"
tags: 1.3 1.5
---

GET_ALL_MODEL_CHANGE_COUNT_VALUES returns the change count values of all existing  models. As the database is accessed directly here, models do not have to be loaded and the model list does not have to be up-to-date. So this command is heplful for cache implementations.

# Syntax:  

```adoscript
{% raw %}
CC "DB"
GET_ALL_MODEL_CHANGE_COUNT_VALUES [ as-map ] .

#--> RESULT ecode:intValue val:strOrMapValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`as-map`|modifier, if specified, the result will be a map, otherwise it will be a token string. A map is more convenient and more efficient for further processing in AdoScript. For a result of a WebSercice call working with a token string might be the better alternative.|

# Returns:  

|`ecode`|intValue|
|`dates`|strOrMapValue; If the result is a map, the map's keys are the model IDs while the map's values are the related change count values. If the result is a token string, for each existing model the val string contains one pair (model ID, change count) whose elements are separated by a tab character ("\t"). These pairs are separated by newline ("\n"). So the complete string has the form "&lt;modelid-1&gt;\t&lt;count-1&gt;\n&lt;modelid-2&gt;\t&lt;count-2&gt;\n...\n&lt;modelid-n&gt;\t&lt;count-n&gt;".|

# Remarks:



# See Also:  



Example 1 (Map):

```adoscript
{% raw %}

CC "Modeling" GET_ACT_MODEL  #--> modelid
CC "DB" GET_ALL_MODEL_CHANGE_COUNT_VALUES as-map  #--> val
SET count:(val[modelid])
CC "AdoScript" INFOBOX ("Change count of current model:" + STR count)

{% endraw %}
```
{: .line-numbers}

Example 2 (Token string):

```adoscript
{% raw %}

CC "Modeling" GET_ACT_MODEL  #--> modelid
CC "DB" GET_ALL_MODEL_CHANGE_COUNT_VALUES  #--> val
SET count:(fortok(t, val, "\n",
                  cond(VAL token(t, 0, "\t") = modelid,
                       set(r, VAL token(t, 1, "\t")), 0)), r)
CC "AdoScript" INFOBOX ("Change count of current model: " + count)

{% endraw %}
```
{: .line-numbers}

