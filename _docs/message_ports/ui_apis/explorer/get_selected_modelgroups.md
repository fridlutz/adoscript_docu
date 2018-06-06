---
layout: commandcall
category: CommandCall
title: "GET_SELECTED_MODELGROUPS"
tags: 1.3 1.5
---

GET_SELECTED_MODELGROUPS returns the IDs of the model groups currently selected in the explorer.

# Syntax:  

```adoscript
{% raw %}
CC "Explorer" GET_SELECTED_MODELGROUPS

#--> RESULT ecode:intValue 
			mgroups:strValue

{% endraw %}
```
{: .line-numbers}

# Parameters:  
none

# Returns:  

|`ecode`|intValue, if everything succeeded, ecode is 0. Otherwise 1 is returned.|
|`mgroups`|strValue, a blank seperated ID list. Possible selected models are not considered.|

# Remarks:



# See Also:  

[GET_SELECTED_MODELS](get_selected_models.html "GET_SELECTED_MODELS")  


Example 1:

```adoscript
{% raw %}

CC "Explorer" GET_SELECTED_MODELGROUPS
SET s:""
FOR i from:0 to:(tokcnt(mgroups, " ") - 1)
{
  CC "Core" GET_MODELGROUP_NAME mgroupid:(VAL token (mgroups, i, " "))
  SET s:(s + cond (i, "\n", "") + mgroupname
}
CC "AdoScript" INFOBOX (s)

{% endraw %}
```
{: .line-numbers}

