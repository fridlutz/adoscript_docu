---
layout: commandcall
category: CommandCall
title: "GET_SELECTED_MODELS"
tags: 1.3 1.5
---

GET_SELECTED_MODELS returns the IDs of the models currently selected in the explorer.

# Syntax:  

```adoscript
{% raw %}
CC "Explorer" GET_SELECTED_MODELS

#--> RESULT	ecode:intValue 
			selmodels:idArray
{% endraw %}
```
{: .line-numbers}

# Parameters:  

none

# Returns:  

|`ecode`|intValue, if everything succeeded, ecode is 0. Otherwise 1 is returned.|
|`selmodels`|idArray, a sorted array of model IDs. Possible selected model group entries are not considered.|

# Remarks:



# See Also:  

[GET_SELECTED_MODELGROUPS](get_selected_modelgroups.html "GET_SELECTED_MODELGROUPS")  


Example 1:

```adoscript
{% raw %}

CC "Explorer" GET_SELECTED_MODELS
SET s:""
FOR i from:0 to:(selmodels.length - 1) {
    CC "Core" GET_MODEL_INFO modelid:(selmodels[i])
    SET s:(s + cond(i, "\n", "") + modelname + " (" + modeltype + ")")
}
CC "AdoScript" INFOBOX (s)

{% endraw %}
```
{: .line-numbers}

