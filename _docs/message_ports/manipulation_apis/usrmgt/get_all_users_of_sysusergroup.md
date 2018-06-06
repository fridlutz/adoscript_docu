---
layout: commandcall
category: CommandCall
title: "GET_ALL_USERS_OF_SYSUSERGROUP"
tags: 1.3 1.5
---

This AdoScript command returns all ADOxx system users of an ADOxx system usergroup.

# Syntax:  

```adoscript
{% raw %}
CC "UserMgt" GET_ALL_USERS_OF_SYSUSERGROUP usergroup:strValue

# --> RESULT ecode:intValue users:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`usergroup`|strValue, the system usergroup which users should be returned|

# Returns:  

|`ecode`|intValue, 0 if the command has been executed successfully, != 0 otherwise.|
|`users`|strValue, the IDs of the system users separated by blanks (' ') that are assigned to this usergroup.|

# Remarks:

This command is available within both the ADOxx Development Toolkit and the ADOxx Modelling Toolkit. In the Modelling Toolkit only users that also have access to the Development Toolkit may call this command! With the messageport command ACTIVATE_READONLY_COMMANDS_FOR_BPMTK this behaviour can be changed.

If a sub-administrator calls this method for a global user group, users of the global group will not be returned, even if the sub-administrator is assigned to the global user group. This is the case, as a sub-administrator only sees users of "his" local user groups.

# See Also:  

[ACTIVATE_READONLY_COMMANDS_FOR_BPMTK](activate_readonly_commands_for_bpmtk.html "ACTIVATE_READONLY_COMMANDS_FOR_BPMTK")  
[LINK_2](link_2.html "LINK_2")  


Example 1:

```adoscript
{% raw %}

CC "UserMgt" GET_ALL_USERS_OF_SYSUSERGROUP usergroup:"Heroes"
IF (ecode = 0)
{
    CC "AdoScript" INFOBOX ("Heroes contains: "+users)
}
ELSE
{
    CC "AdoScript" ERRORBOX "Could not get users of usergroup Heroes!"
}

{% endraw %}
```
{: .line-numbers}

