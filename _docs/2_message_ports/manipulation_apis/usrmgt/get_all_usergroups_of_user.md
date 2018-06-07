---
layout: commandcall
category: CommandCall
title: "GET_ALL_USERGROUPS_OF_USER"
tags: 1.3 1.5
---

GET_ALL_USERGROUPS_OF_USER returns all user groups of a given ADOxx user.

# Syntax:  

```adoscript
{% raw %}
CC "UserMgt" GET_ALL_USERGROUPS_OF_USER user:strValue [ sep:strValue ]

# --> RESULT usergroups:strValue ecode:intValue 
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`user`|strValue, the username|
|`sep`|strValue|

# Returns:  

|`ecode`|intValue, 0 (meaning success) or 1 (meaning error).|
|`usergroups`|strValue, contains user group names separated by by the character passed with sep. The default value for sep is ";" (semicolon). However, it is recommended to use sep:"\t" (TAB).|

# Remarks:

This command is available within both the ADOxx Development Toolkit and the ADOxx Modelling Toolkit. In the Modelling Toolkit only users that also have access to the Development Toolkit may call this command! With the messageport command ACTIVATE_READONLY_COMMANDS_FOR_BPMTK this behaviour can be changed.

# See Also:  

[ACTIVATE_READONLY_COMMANDS_FOR_BPMTK](activate_readonly_commands_for_bpmtk.html "ACTIVATE_READONLY_COMMANDS_FOR_BPMTK")  


Example 1:

```adoscript
{% raw %}

CC "UserMgt" GET_ALL_USERGROUPS_OF_USER user:"Nimda" sep:"\t"
IF (ecode) {
    CC "AdoScript" ERRORBOX "Error!"
}

{% endraw %}
```
{: .line-numbers}

