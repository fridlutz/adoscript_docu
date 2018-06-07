---
layout: commandcall
category: CommandCall
title: "GET_SYSUSER_SETTINGS"
tags: 1.3 1.5
---

This AdoScript command returns the name of the attached application library and the user specific information.

# Syntax:  

```adoscript
{% raw %}
CC "UserMgt" GET_SYSUSER_SETTINGS userid:intValue

#--> RESULT ecode:intValue applibname:strValueuserspecinfo:strValue
			sub-admin:boolValueadmtk:boolValue bpmtk:boolValue.
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`userid`|intValue, the ID of the system user.|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`applibname`|strValue, the name of the application library that is attached to the system user|
|`userspecinfo`|strValue, the user specific info string (can optionally be filled when creating users).|
|`bpmtk`|boolValue, Has the user access to the ADOxx Modelling Toolkit? 0 = no, 1 = yes.|
|`admtk`|boolValue, Has the user access to the ADOxx Development Toolkit? 0 = no, 1 = yes.|
|`sub-admin`|boolValue, Is the system user a Sub-Administrator? 0 = no, 1 = yes.|

# Remarks:

This command is available within both the ADOxx Development Toolkit and the ADOxx Modelling Toolkit. In the Modelling Toolkit only users that also have access to the Development Toolkit may call this command!

With the messageport command ACTIVATE_READONLY_COMMANDS_FOR_BPMTK  this behaviour can be changed.

# See Also:  

[ACTIVATE_READONLY_COMMANDS_FOR_BPMTK](activate_readonly_commands_for_bpmtk.html "ACTIVATE_READONLY_COMMANDS_FOR_BPMTK")  
[LINK_2](link_2.html "LINK_2")  


Example 1:

```adoscript
{% raw %}

# get attached library of system user with ID 4711
CC "UserMgt" GET_SYSUSER_SETTINGS userid:4711
IF (ecode = 0)
{
  CC "AdoScript" INFOBOX ("Library: " + applibname)
}

{% endraw %}
```
{: .line-numbers}

