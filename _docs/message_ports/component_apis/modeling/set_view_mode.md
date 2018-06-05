---
layout: commandcall
category: CommandCall
title: "SET_VIEW_MODE"
tags: 1.3 1.5
---

SET_VIEW_MODE sets the current modename in the model passed with modelid.

# Syntax:  

```adoscript
{% raw %}
CC "Modeling" SET_VIEW_MODE [ modelid:modelId ] mode-name:strValue .


# --> RESULT ecode:intValue

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|modelId|
|`mode-name`|strValue|

# Returns:  

|`ecode`|intValue, the return value ecode is set to 0 if the the command worked, to 1 if an error occured.|


# Remarks:

If no modelid is passed, the current active model will be taken.



# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Modeling" GET_ALL_VIEW_MODES
CC "Modeling" SET_VIEW_MODE mode-name:(token(modename,1,"\n"))

{% endraw %}
```
{: .line-numbers}
Sets the current view mode to the second view mode in the current active model

