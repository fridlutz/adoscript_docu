---
layout: commandcall
category: CommandCall
title: "ALIGN_SELECTED"
tags: 1.3 1.5
---

ALIGN_SELECTED aligns the selected objects in the model passed with modelid vertically or horizontally.

# Syntax:  

```adoscript
{% raw %}
CC "Modeling" ALIGN_SELECTED [ modelid:modelId ] Align .


Align : vertically | horizontally .


# --> RESULT ecode:intValue .

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|modelId|
|`vertically`|modifier|
|`horizontally`|modifier|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|


# Remarks:

If no modelid is passed, the current active model will be taken.  
The object to align to should have the focus.

The return value ecode is set to 0 if the the command worked, to 1 if an error occured.

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Modeling" SELECT_ALL
CC "Core" GET_ALL_OBJS modelid:(VAL modelid)
CC "Modeling" SET_FOCUS_NODE objid:(VAL token(objids, 1, " "))
CC "Modeling" ALIGN_SELECTED horizontally

{% endraw %}
```
{: .line-numbers}


