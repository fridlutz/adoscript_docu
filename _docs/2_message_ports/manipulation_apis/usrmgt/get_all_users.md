---
layout: commandcall
category: CommandCall
title: "GET_ALL_USERS"
tags: 1.3 1.5
---

GET_ALL_USERS returns the names of all users.

# Syntax:  

```adoscript
{% raw %}
CC "UserMgt" GET_ALL_USERS [ sep:strValue ]

# --> RESULT users:strValue ecode:intValue .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`sep`|strValue|

# Returns:  

|`ecode`|intValue, 0 (meaning success) or 1 (meaning error).|
|`users`|strValue, containsuser names separated by by the character passed with sep. The default value for sep is ";" (semicolon). However, it is recommended to use sep:"\t" (TAB).|

# Remarks:

This command is available within both the ADOxx Development Toolkit and the ADOxx Modelling Toolkit.

# See Also:  



Example:

