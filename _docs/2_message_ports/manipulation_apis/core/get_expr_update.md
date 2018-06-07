---
layout: commandcall
category: CommandCall
title: "GET_EXPR_UPDATE"
tags: 1.3 1.5
---

The command GET_EXPR_UPDATE returns the current settings of the expression manager.

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_EXPR_UPDATE

#--> RESULT ecode:intValue 
			synchronous:( "on" | "off" ) 
			asynchronous:( "on" | "off" ) 
			count:intValue 
			interval:intValue 
			counttotal:intValue 
			countstale:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

none

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`synchronous`|strValue, "on" or "off"|
|`asynchronous`|strValue "on" or	"off"|
|`count`|intValue|
|`interval`|intValue|
|`counttotal`|intValue, returns the total number of expressions that are currently managed (all expression attributes of all opened models).|
|`countstale`|intValue, returns the number of stale expressions, expressions stat still have to be updated.|

# Remarks:

Compare the arguments of SET_EXPR_UPDATE for the meaning of the return values.

# See Also:

[GET_EXPR_UPDATE](get_expr_update.html "GET_EXPR_UPDATE")  


