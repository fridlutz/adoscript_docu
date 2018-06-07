---
layout: commandcall
category: CommandCall
title: "SET_ENV_STRING"
tags: 1.3 1.5
---

SET_ENV_STRING is used to add an environment variable.

# Syntax:  

```adoscript
{% raw %}
CC "Core" SET_ENV_STRING envvar:strValue envstr:strValue. 

#--> RESULT ecode:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`envvar`|strValue, the name of the environment variable|
|`envstr`|strValue, the new value of the environment variable|

# Returns:  

|`ecode`|intValue, -1 in case of error or 0 in case of success.|

# Remarks:

This function has no effect on AdoScript internal variables!

# See Also:  

[GET_ENV_STRING](get_env_string.html "GET_ENV_STRING")  


