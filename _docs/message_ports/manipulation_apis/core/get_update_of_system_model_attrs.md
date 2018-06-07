---
layout: commandcall
category: CommandCall
title: "GET_UPDATE_OF_SYSTEM_MODEL_ATTRS"
tags: 1.3 1.5
---

GET_UPDATE_OF_SYSTEM_MODEL_ATTRS returns the current status (enabled or disabled) of the "update of system model attributes" flag.

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_UPDATE_OF_SYSTEM_MODEL_ATTRS

#-->RESULT ecode:intValue val:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

none

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`val`|intValue, 0 for sidabled or 1 for enabled|

# Remarks:

See SET_UPDATE_OF_SYSTEM_MODEL_ATTRS for more information.

# See Also:  

[SET_UPDATE_OF_SYSTEM_MODEL_ATTRS](set_update_of_system_model_attrs.html "SET_UPDATE_OF_SYSTEM_MODEL_ATTRS")  


Example:

