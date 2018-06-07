---
layout: commandcall
category: CommandCall
title: "GET_ALL_USERGROUPS_OF_CURRENT_SYSUSER"
tags: 1.3 1.5
---

GET_ALL_USERGROUPS_OF_CURRENT_SYSUSER returns the names of all user groups the current  ADOxx system user belongs to.

# Syntax:  

```adoscript
{% raw %}
CC "UserMgt" GET_ALL_USERGROUPS_OF_CURRENT_SYSUSER [ sep:strValue ] .


# --> RESULT ecode:intValue usergroups:strValue .

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`sep`|strValue|

# Returns:  

|`ecode`|intValue, 0 (meaning success) or != 0 (meaning error).|
|`usergroups`|strValue, contains user group names separated by the character passed with sep. The default value for sep is ";" (semicolon). However, 	it is recommended to use sep:"\t" (TAB).|


# Remarks:

This command is available within both the ADOxx Development Toolkit and the ADOxx Modelling Toolkit.

# See Also:  



Example:

