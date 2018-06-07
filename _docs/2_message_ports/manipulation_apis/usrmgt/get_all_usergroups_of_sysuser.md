---
layout: commandcall
category: CommandCall
title: "GET_ALL_USERGROUPS_OF_SYSUSER"
tags: 1.3 1.5
---

GET_ALL_USERGROUPS_OF_SYSUSER returns all user groups of a given ADOxx system user.

# Syntax:  

```adoscript
{% raw %}
CC "UserMgt" GET_ALL_USERGROUPS_OF_SYSUSER UserSpec [ sep:strValue ]

UserSpec : UserByName | UserByID .

UserByName : user:strValue domain:strValue[ ignore-case ] .

UserByID : userid:intValue .
{% endraw %}
```
{: .line-numbers}

```adoscript
{% raw %}
# --> RESULT ecode:intValue usergroups:strValue .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`user`|strValue, the display name of the user and|
|`domain`|strValue, the display name of the domain of the user|
|`ignore-case`|modifier, if given, case is ignored concerning the user display name. This means that it does not matter if the user name is given in upper or lower case (or mixed). If a user with such a name exists, its user groups will be returned anyway.|
|`userid`|intValue, the ID of the system user.|
|`sep`|strValue|

# Returns:  

|`ecode`|intValue, 0 (meaning success) or != 0 (meaning error).|
|`usergroups`|strValue, contains user group names separated by the character passed with sep. The default value for sep is ";" (semicolon). However, it is recommended to use sep:"\t" (TAB).|

# Remarks:

This command is available within both the ADOxx Development Toolkit and the ADOxx Modelling Toolkit. In the Modelling Toolkit only users that also have access to the Development Toolkit may call this command! With the messageport command ACTIVATE_READONLY_COMMANDS_FOR_BPMTK this behaviour can be changed.

# See Also:  

[ACTIVATE_READONLY_COMMANDS_FOR_BPMTK](activate_readonly_commands_for_bpmtk.html "ACTIVATE_READONLY_COMMANDS_FOR_BPMTK")  


Example 1:

```adoscript
{% raw %}

CC "UserMgt" GET_ALL_USERGROUPS_OF_SYSUSER
        user:"Nimda" domain:"NimdaDomain" sep:"\t"
IF (ecode) {
    CC "AdoScript" ERRORBOX "Error!"
}

{% endraw %}
```
{: .line-numbers}

