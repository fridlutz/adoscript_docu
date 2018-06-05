---
layout: commandcall
category: CommandCall
title: "GET_ALL_USERS_OF_USERGROUP"
tags: 1.3 1.5
---

GET_ALL_USERS_OF_USERGROUP returns the names of all users belonging to a certain user group.

# Syntax:  

```adoscript
{% raw %}
CC "UserMgt" GET_ALL_USERS_OF_USERGROUP usergroup:strValue [ sep:strValue ] .


# --> RESULT users:strValue ecode:intValue .

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`usergroup`|strValue, the usergroup which users should be returned.|
|`sep`|strValue|

# Returns:  

|`ecode`|intValue, 0 (meaning success) or 1 (meaning error).|
|`users`|strValue, the names of the users separated by semicolon (';') assigned to this usergroup.|

# Remarks:

It is recommended to use sep:"\t" (TAB).

This command is available within both the ADOxx Development Toolkit and the ADOxx Modelling Toolkit. In the Modelling Toolkit only users that also have access to the Development Toolkit may call this command! With the messageport command ACTIVATE_READONLY_COMMANDS_FOR_BPMTK this behaviour can be changed.

If a sub-administrator calls this method for a global user group, users of the global group will not be returned, even if the sub-administrator is assigned to the global user group. This is the case, as a sub-administrator only sees users of "his" local user groups.

# See Also:  

[ACTIVATE_READONLY_COMMANDS_FOR_BPMTK](activate_readonly_commands_for_bpmtk.html "ACTIVATE_READONLY_COMMANDS_FOR_BPMTK")  


Example 1:

```adoscript
{% raw %}

CC "UserMgt" GET_ALL_USERS_OF_USERGROUP usergroup:"MyGroup" sep:"\t"
IF (ecode) {
    CC "AdoScript" ERRORBOX "Error!"
}

{% endraw %}
```
{: .line-numbers}



