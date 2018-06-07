---
layout: commandcall
category: CommandCall
title: "UPDATE_EXPR_ATTRS"
tags: 1.3 1.5
---

UPDATE_EXPR_ATTRS forces alle EXPRESSION attributes of a certain model to be updated. This means that all expression results will get correct values.

# Syntax:  

```adoscript
{% raw %}
CC "Core" UPDATE_EXPR_ATTRS	modelid:strValue [ synchronous:boolValue ]

#-->RESULT ecode:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|intValue, the ID of the model.|
|`synchronous`|1|0, specify whether the expressions should be updated instantly (which is the default) or later in the background.|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|

# Remarks:



# See Also:

