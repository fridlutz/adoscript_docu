---
layout: commandcall
category: CommandCall
title: "GET_MODEL_LIST_CHANGE_COUNT"
tags: 1.3 1.5
---

GET_MODEL_LIST_CHANGE_COUNT returns a counter value which can be used to determine whether changes in the model list exist on database level.

# Syntax:  

```adoscript
{% raw %}
CC "DB" GET_MODEL_LIST_CHANGE_COUNT

#--> RESULT ecode:intValue 
			val:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

none

# Returns:  

|`ecode`|intValue, 0 if everything went ok != 0 otherwise.|
|`val`|intValue,|

# Remarks:

To find out whether something changed in the model list between a time t1 and a time t2, GET_MODEL_LIST_CHANGE_COUNT has to be called at both times. If the returned values are different, changes in the model list exist on data base level.

Changes in the model list are caused by the following actions  
* create, delete, rename, copy or move a model group
* create, delete, copy or move a model reference (reference from model group to model)
* create, delete, rename or copy a model
* change the user group acces rights of a model group
* change the value of the model attribute, which is additionally displayed in model select boxes


# See Also:  

[GET_USER_LIST_CHANGE_COUNT](get_user_list_change_count.html "GET_USER_LIST_CHANGE_COUNT")  
[GET_AP_CHANGE_COUNT](get_ap_change_count.html "GET_AP_CHANGE_COUNT")  


