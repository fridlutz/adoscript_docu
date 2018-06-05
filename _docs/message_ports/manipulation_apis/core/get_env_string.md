---
layout: commandcall
category: CommandCall
title: "GET_ENV_STRING"
tags: 1.3 1.5
---

GET_ENV_STRING returns the value of an environment variable.  


# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_ENV_STRING envvar:strValue .

#--> RESULT envstr:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`envvar`|strValue, the name of the environment variable|

# Returns:  

|`ecode`|intValue, contains the error code or is 0 in case of success.|
|`envvar`|strValue, the value of the variable.|

# Remarks:

In a Windows System Shell, all environment variables can be displayed with the command SET

# See Also:  

[SET_ENV_STRING](set_env_string.html "SET_ENV_STRING")  


