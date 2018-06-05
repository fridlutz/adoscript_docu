---
layout: commandcall
category: CommandCall
title: "GET_USERGROUP_TYPE"
tags: 1.3 1.5
---

This AdoScript command returns the information if the given user group is a global user group or not (if not global, it is a local user group).

# Syntax:  

```adoscript
{% raw %}
CC "UserMgt" GET_USERGROUP_TYPE	usergroupid:intValue

# --> RESULT ecode:intValue global:boolValue 
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`usergroupid`|intValue, the user group for which the information is queried.|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`global`|boolValue, if the user group is a global group or not (0: no, 1: yes).|

# Remarks:

This command works for both internal and system user groups!

This command is available within both the ADOxx Development Toolkit and the ADOxx Modelling Toolkit. In the Modelling Toolkit only users that also have access to the Development Toolkit may call this command!  
With the messageport command ACTIVATE_READONLY_COMMANDS_FOR_BPMTK  this behaviour can be changed.

# See Also:  

[ACTIVATE_READONLY_COMMANDS_FOR_BPMTK](activate_readonly_commands_for_bpmtk.html "ACTIVATE_READONLY_COMMANDS_FOR_BPMTK")  


Example 1:

```adoscript
{% raw %}

# check type of user group "Heroes"
CC "UserMgt" GET_USERGROUP_ID usergroup:"Heroes"
IF (ecode = 0)
{
  CC "UserMgt" GET_USERGROUP_TYPE usergroupid:(usergroupid)
  IF (global = 1)
  {
    CC "AdoScript" INFOBOX ("Heroes is a global user group!")
  }
}

{% endraw %}
```
{: .line-numbers}

