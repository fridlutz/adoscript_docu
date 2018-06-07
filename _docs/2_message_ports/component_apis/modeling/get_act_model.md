---
layout: commandcall
category: CommandCall
title: "GET_ACT_MODEL"
tags: 1.3 1.5
---

Is a command call of the message port "Modeling" and returns the modelid of the model that is currently opened and active (visible, on top) in the model editor.

# Syntax:  
```adoscript
{% raw %}
  CC "Modeling" GET_ACT_MODEL

{% endraw %}
```
{: .line-numbers}

# Parameters:  

none

# Returns:  

|`modelid`|the modelid of the model that is currently opened and active (visible, on top) in the model editor (integer)|

# Remarks:

The difference to the command GET_ACTIVE_MODEL is that you can use GET_ACT_MODEL with CC, while GET_ACTIVE_MODEL can just be called using SEND.  
If no model window is active (i.e. no model window exists), the retured modelid has the value -1.


# See Also:  

[GET_MODEL_INFO](get_model_info.html "GET_MODEL_INFO")  


Example 1:

```adoscript
{% raw %}
CC "Modeling" GET_ACT_MODEL
IF (modelid != -1) {
    CC "Core" GET_MODEL_INFO modelid:(modelid)
    CC "AdoScript" INFOBOX ("The curent active model is \"" + modelname + "\"")
} ELSE {
    CC "AdoScript" INFOBOX ("Currently no model window exists.")
}

{% endraw %}
```
{: .line-numbers}

Queries the ID of the current active model. From the id the model name is retrieved and displayed in an infobox.  
