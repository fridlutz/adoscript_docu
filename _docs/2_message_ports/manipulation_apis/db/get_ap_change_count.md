---
layout: commandcall
category: CommandCall
title: "GET_AP_CHANGE_COUNT"
tags: 1.3 1.5
---

GET_AP_CHANGE_COUNT returns a counter value which can be used to determine whether attribute profile changes exist on database level.

# Syntax:  

```adoscript
{% raw %}
CC "DB" GET_AP_CHANGE_COUNT

#--> RESULT ecode:intValue val:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

none

# Returns:  

|`ecode`|intValue, 0 if everything went ok != 0 otherwise.|
|`val`|intValue,|

# Remarks:

To find out whether atribute profiles have been changed between a time t1 and a time t2, GET_AP_CHANGE_COUNT has to be called at both times. If the returned values are different, attribute profile changes exist on data base level.

Attribute profile changes are caused by the following actions  
* create, delete, rename, copy or move an attribute profile group
* create, delete, copy or move an attribute profile
* change an attribute value of an attribute profile

# See Also:  

[GET_MODEL_LIST_CHANGE_COUNT](get_model_list_change_count.html "GET_MODEL_LIST_CHANGE_COUNT")  
[GET_USER_LIST_CHANGE_COUNT](get_user_list_change_count.html "GET_USER_LIST_CHANGE_COUNT")  


