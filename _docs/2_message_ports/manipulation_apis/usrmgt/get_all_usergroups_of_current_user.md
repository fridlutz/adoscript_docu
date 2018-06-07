---
layout: commandcall
category: CommandCall
title: "GET_ALL_USERGROUPS_OF_CURRENT_USER"
tags: 1.3 1.5
---

GET_ALL_USERGROUPS_OF_CURRENT_USER returns the names of all user groups the current ADOxx user belongs to.

# Syntax:  

```adoscript
{% raw %}
CC "UserMgt" GET_ALL_USERGROUPS_OF_CURRENT_USER [ sep:strValue ]

# --> RESULT usergroups:strValue ecode:intValue 
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`sep`|strValue|

# Returns:  

|`ecode`|intValue, 0 (meaning success) or 1 (meaning error).|
|`usergroups`|strValue, contains user group names separated by the character passed with sep. The default value for sep is ";" (semicolon). However, it is recommended to use sep:"\t" (TAB).|

# Remarks:

This command does not work with system users.

This command is available within both the ADOxx Development Toolkit and the ADOxx Modelling Toolkit.

# See Also:  



Example:

