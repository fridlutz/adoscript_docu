---
layout: commandcall
category: CommandCall
title: "GET_VISIBLE_RELATIONS"
tags: 1.3 1.5
---



# Syntax:  

```adoscript
{% raw %}
CC "Modeling" GET_VISIBLE_RELATIONS [ modelid:modelId ] .


# --> RESULT ecode:intValue relationids:strValue

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|modelId|

# Returns:  

|`ecode`|intValue, the return variable ecode is set to 0 if the the command succeeded, otherwise to 1.|
|`relationids`|strValue|

# Remarks:

The model ID is specified with modelid. If no modelid is passed, the current active model will be taken.

The visible relation classes are returned as string of IDs as return variable relationids.


# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Modeling" debug GET_VISIBLE_RELATIONS

{% endraw %}
```
{: .line-numbers}
Shows all relationids in the current active model

