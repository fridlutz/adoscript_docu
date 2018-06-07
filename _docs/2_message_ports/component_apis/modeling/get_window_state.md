---
layout: commandcall
category: CommandCall
title: "GET_WINDOW_STATE"
tags: 1.3 1.5
---

GET_WINDOW_STATE returns the state of the model window with the passed modelid.

# Syntax:  

```adoscript
{% raw %}
CC "Modeling" GET_WINDOW_STATE [ modelid:intValue ] .


# --> RESULT ecode:intValue state:strVal (max|min|normal)

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|intValue|

# Returns:  

|`ecode`|intValue, the return variable ecode is set to 0 if setting worked, to 1 if an error occured.|
|`state`|strVal|

# Remarks:

If no modelid is passed, the current active model will be taken. The return value state contains "max", "min" or "normal".

Only 1 window can be maximized. The status of the other windows is normal or min.



# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Modeling" debug GET_WINDOW_STATE

{% endraw %}
```
{: .line-numbers}
Shows the current model window state.

