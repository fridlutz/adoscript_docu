---
layout: commandcall
category: CommandCall
title: "GET_OBJECTS_WITHIN_AREA"
tags: 1.3 1.5
---

GET_OBJECTS_WITHIN_AREA returns all objects in the objids array and all relations in the relationids array in the model passes with modelid.

# Syntax:  

```adoscript
{% raw %}
CC "Modeling" GET_OBJECTS_WITHIN_AREA [ modelid:modelId ] x1:measureValue y1:measureValue 
                                                          x2:measureValue y2:measureValue.


# -->	RESULT ecode:intValue objids:strValue relationids:strValue

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|modelId|
|`x1`|measureValue|
|`y1`|measureValue|
|`x2`|measureValue y2:measureValue.|

# Returns:  

|`ecode`|intValue, the return value ecode is set to 0 if the the command worked, to 1 if an error occured.|
|`objids`|strValue|
|`relationids`|strValue|

# Remarks:

If no modelid is passed, the current active model will be taken. The Area is passed with x1,y1,x2 and y2 as measure values.



# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Modeling" debug GET_OBJECTS_WITHIN_AREA x1:1cm y1:1cm x2:20cm y2:20cm

{% endraw %}
```
{: .line-numbers}
Shows all object and relationids in the area 1cm, 1cm to 20cm, 20cm

