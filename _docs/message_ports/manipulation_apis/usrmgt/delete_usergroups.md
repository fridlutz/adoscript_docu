---
layout: commandcall
category: CommandCall
title: "DELETE_USERGROUPS"
tags: 1.3 1.5
---

DELETE_USERGROUPS deletes one or more ADOxx user groups.

# Syntax:  

```adoscript
{% raw %}
CC "UserMgt" DELETE_USERGROUPS usergroups:strValue [ sep:strValue ]

# --> RESULT ecode:intValue .

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`usergroups`|strValue, specifies the names of one or more user groups to be deleted. The user groups are specified as a string containing usergroup names, separated by the character passed with sep. The default value for sep is ";" (semicolon). However, it is recommended to use sep:"\t" (TAB).|
|`sep`|strValue|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|

# Remarks:

This command is only available within the ADOxx Development Toolkit.

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "UserMgt" DELETE_USERGROUPS usergroups:"group1\tgroup2" sep:"\t"
IF (ecode) {
    CC "AdoScript" ERRORBOX "User groups could not be deleted!"
}

{% endraw %}
```
{: .line-numbers}


