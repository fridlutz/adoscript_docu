---
layout: commandcall
category: CommandCall
title: "GET_DATE_OF_LAST_CHANGE"
tags: 1.3 1.5
---

GET_DATE_OF_LAST_CHANGE returns the date of last change of a model. As the database is accessed directly here, the model does not have to be loaded and the model list does not have to be up-to-date. So this command is helpful for cache implementations.

# Syntax:  

```adoscript
{% raw %}
CC "DB" GET_DATE_OF_LAST_CHANGE	modelid:id [ accuracy:"min"|"sec" ]

#--> RESULT ecode:intValue date:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|intValue, the ID of the model|
|`accuracy`|strValue, "min" | "sec"|

# Returns:  

none

# Remarks:

By default, the returned date has the format "DD.MM.YYYY,HH:MM:SS". This can be changed with the parameter accuracy. If "min" is passed for accuracy, then each date value will not include seconds and will have the format "DD.MM.YYYY,HH:MM". The parameter value "sec" for accuracy is the default and includes seconds in the returned date.

In opposite to the "last change date" model attribute, there is no blank contained in the returned date string.

# See Also:  



Example:  

