---
layout: commandcall
category: CommandCall
title: "GET_SYSUSER_ACCESS_STR"
tags: 1.3 1.5
---

This AdoScript command returns the current access string of an ADOxx system user.

# Syntax:  

```adoscript
{% raw %}
CC "UserMgt" GET_SYSUSER_ACCESS_STR	user:strValue domain:strValue [ ignore-case ] | userid:intValue

# --> RESULT ecode:intValue accessstr - strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`user`|strValue, the display name of the user and|
|`domain`|strValue, the display name of the domain of the user|
|`ignore-case`|modifier, if given, case is ignored concerning the user display name. This means that it does not matter if the user name is given in upper or lower case (or mixed). If a user with such a name exists, its access string will be returned anyway.|
|`userid`|intValue, the ID of the system user.|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`accessstr`|strValue, contains the current access rights of this user.|

# Remarks:

This command is available within both the ADOxx Development Toolkit and the ADOxx Modelling Toolkit. In the Modelling Toolkit only users that also have access to the Development Toolkit may call this command!  
With the messageport command ACTIVATE_READONLY_COMMANDS_FOR_BPMTK  this behaviour can be changed.

# See Also:  

[ACTIVATE_READONLY_COMMANDS_FOR_BPMTK](activate_readonly_commands_for_bpmtk.html "ACTIVATE_READONLY_COMMANDS_FOR_BPMTK")  


Example 1:

```adoscript
{% raw %}

CC "UserMgt" GET_SYSUSER_ACCESS_STR user:"Superman" domain:"SuperDomain"
IF (ecode = 0)
{
    CC "AdoScript" INFOBOX (accessstr)
}
ELSE
{
    CC "AdoScript" ERRORBOX "Could not get user access string!"
    EXIT
}

{% endraw %}
```
{: .line-numbers}

