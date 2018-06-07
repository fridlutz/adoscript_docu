---
layout: commandcall
category: CommandCall
title: "GET_VISIBLE_CLASSES"
tags: 1.3 1.5
---

GET_VISIBLE_CLASSES returns all classes which are currently visible in a model.

# Syntax:  

```adoscript
{% raw %}
CC "Modeling" GET_VISIBLE_CLASSES [ modelid:modelId ] .


# --> RESULT ecode:intValue classids:strValue

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|modelId, the model ID is specified with modelid.|

# Returns:  

|`ecode`|intValue, the return variable ecode is set to 0 if the the command succeeded, otherwise to 1.|
|`classids`|strValue|

# Remarks:

If no modelid is passed, the current active model will be taken.

The visible classes are returned as string of IDs as return variable classids.


# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Modeling" debug GET_VISIBLE_CLASSES

{% endraw %}
```
{: .line-numbers}
Shows all classes in the current active model

