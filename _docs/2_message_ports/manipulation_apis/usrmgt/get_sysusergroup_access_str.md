---
layout: commandcall
category: CommandCall
title: "GET_SYSUSERGROUP_ACCESS_STR"
tags: 1.3 1.5
---

This AdoScript command returns the current access string of an ADOxx system usergroup.

# Syntax:  

```adoscript
{% raw %}
CC "UserMgt" GET_SYSUSERGROUP_ACCESS_STR usergroup:strValue

# --> RESULT ecode:intValue accessstr:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`usergroup`|strValue, the name of the usergroup|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`accessstr`|strValue, contains the current access rights of this usergroup.|

# Remarks:

The syntax of the usergroup access string is not published. This command is only to get an access string from a certain usergroup and assign those access rights to another ADOxx system usergroup.

This command is available within both the ADOxx Development Toolkit and the ADOxx Modelling Toolkit. In the Modelling Toolkit only users that also have access to the Development Toolkit may call this command!  
With the messageport command ACTIVATE_READONLY_COMMANDS_FOR_BPMTK  this behaviour can be changed.

# See Also:  

[ACTIVATE_READONLY_COMMANDS_FOR_BPMTK](activate_readonly_commands_for_bpmtk.html "ACTIVATE_READONLY_COMMANDS_FOR_BPMTK")  


Example 1:

```adoscript
{% raw %}

CC "UserMgt" GET_SYSUSERGROUP_ACCESS_STR usergroup:"SysAdmins"
IF (ecode = 0)
{
    CC "AdoScript" INFOBOX (accessstr)
}
ELSE
{
    CC "AdoScript" ERRORBOX "Could not get the access string of the usergroup SysAdmins!"
    EXIT
}

{% endraw %}
```
{: .line-numbers}

