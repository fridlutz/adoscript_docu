---
layout: commandcall
category: CommandCall
title: "GET_MODIFIED_COUNT"
tags: 1.3 1.5
---

GET_MODIFIED_COUNT returns the number of unsaved changes of a model.

# Syntax:  

```adoscript
{% raw %}
CC "Modeling" GET_MODIFIED_COUNT	 [ id ] .


# --> RESULT modified:intValue .

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`id`|modifier, the ID must be a model ID.|

# Returns:  

|`modified`|intValue|

# Remarks:

If no ID is specified, the command is applied on the active model window.  
The modified result value states the modification count of the specified model. A value of 0 means that the model is not modified.  
Attention: Just changes via the modeling component are counted here. Do not rely on the modeling component's change counter where modifications by core component calls (e.g. CC "Core" SET_ATTRIUTE_VALUE ...) could have been performed.

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Modeling" GET_MODIFIED_COUNT
IF (modified) {
    CC "Modeling" SAVE
}

{% endraw %}
```
{: .line-numbers}


