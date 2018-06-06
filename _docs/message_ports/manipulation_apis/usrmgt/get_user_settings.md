---
layout: commandcall
category: CommandCall
title: "GET_USER_SETTINGS"
tags: 1.3 1.5
---

This AdoScript command returns the name of the attached application library and the user specific information.

# Syntax:  

```adoscript
{% raw %}
    CC "UserMgt" GET_USER_SETTINGS userid:intValue


# --> RESULT ecode:intValue applibname:strValue userspecinfo:strValue
	sub-admin:boolValueadmtk:boolValue bpmtk:boolValue.

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`userid`|intValue, the user for which the information is queried.|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`applibname`|strValue, the name of the application library|
|`userspecinfo`|strValue, the user specific info string (can optionally be filled when creating users).|
|`bpmtk`|boolValue, Has the user access to the ADOxx Modelling Toolkit? 0 = no, 1 = yes.|
|`admtk`|boolValue, Has the user access to the ADOxx Development Toolkit? 0 = no, 1 = yes.|
|`sub-admin`|boolValue, Is the system user a Sub-Administrator? 0 = no, 1 = yes.|

# Remarks:

This command is available within both the ADOxx Development Toolkit and the ADOxx Modelling Toolkit. In the Modelling Toolkit only users that also have access to the Development Toolkit may call this command!  
With the messageport command ACTIVATE_READONLY_COMMANDS_FOR_BPMTK  this behaviour can be changed.

# See Also:  

[ACTIVATE_READONLY_COMMANDS_FOR_BPMTK](activate_readonly_commands_for_bpmtk.html "ACTIVATE_READONLY_COMMANDS_FOR_BPMTK")  


Example 1:

```adoscript
{% raw %}

# get library of user "Superman"
CC "UserMgt" GET_USER_ID user:"Superman"
IF (ecode = 0)
{
  CC "UserMgt" GET_USER_SETTINGS userid:(userid)
  IF (ecode = 0)
  {
    CC "AdoScript" INFOBOX ("Library: " + applibname)
  }
}

{% endraw %}
```
{: .line-numbers}

