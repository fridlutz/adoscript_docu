---
layout: commandcall
category: CommandCall
title: "ADD_SYSUSERS_TO_GROUPS"
tags: 1.3 1.5
---

ADD_SYSUSERS_TO_GROUPS assigns one or more ADOxx system users to one or more system user groups.

# Syntax:  

```adoscript
{% raw %}
CC "UserMgt" ADD_SYSUSERS_TO_GROUPS	userids:strValue usergroups:strValue
									[ sep:strValue ] .


# --> RESULT ecode:intValue .

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`userids`|strValue|
|`usergroups`|strValue|
|`sep`|strValue|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|


# Remarks:

usergroups is a string containing usergroup names, separated by the character passed with sep. The default value for sep is ";" (semicolon). However, it is recommended to use sep:"\t" (TAB).

The returned error code ecode is 0 if the command has been executed successfully. Any other value means that an error occured, e.g. if a specified user does not exist.

Note: This command is available within both the Development Toolkitand the Modelling Toolkit.  
In the Modelling Toolkit usually only users that also have access to the Development Toolkit can call this command. However, with ACTIVATE_READONLY_COMMANDS_FOR_BPMTK this command can be activated also for non-admins (although it is actually not a readonly command).

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "UserMgt" ADD_SYSUSERS_TO_GROUPS
        userids:"47111 47112"
        usergroups:"SysGroup1\tSysGroup2" sep:"\t"

{% endraw %}
```
{: .line-numbers}
assigns the system users with IDs 47111 and 47112 to the system user groupsSysGroup1and SysGroup2.

