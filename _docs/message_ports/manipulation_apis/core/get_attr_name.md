---
layout: commandcall
category: CommandCall
title: "GET_ATTR_NAME"
tags: 1.3 1.5
---

GET_ATTR_NAME returns the name of an attribute which is specified by ID.

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_ATTR_NAME attrid:id .


#-->RESULT ecode:intValue attrname:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`attrid`|id, the ID of the attribute is passed as argument attrid.|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`attrname`|strValue, the return variable attrname is set to the name of the attribute.|

# Remarks:




# See Also:  



Example:

