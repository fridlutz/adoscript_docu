---
layout: commandcall
category: CommandCall
title: "REMOVE_SYSUSERS_FROM_GROUPS"
tags: 1.3 1.5
---

REMOVE_SYSUSERS_FROM_GROUPS removes one or more ADOxx system users from one or more groups.

# Syntax:  

```adoscript
{% raw %}
CC "UserMgt" REMOVE_SYSUSERS_FROM_GROUPS userids:strValue
										 usergroups:strValue 
										 [ sep:strValue ]

# --> RESULT ecode:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`userids`|strValue, string containing userids separated by " " (blank)|
|`usergroups`|strValue, one or more usergroup names, separated by the character passed with sep. The default value for sep is ";" (semicolon). However, it is recommended to use sep:"\t" (TAB).|
|`sep`|strValue|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|


# Remarks:

This command is available within both the ADOxx Development Toolkit and the ADOxx Modelling Toolkit. In the Modelling Toolkit only users that also have access to the Development Toolkit may call this command!  
However, with ACTIVATE_READONLY_COMMANDS_FOR_BPMTK this command can be activated also for non-admins (although it is actually not a readonly command).

# See Also:  

[ACTIVATE_READONLY_COMMANDS_FOR_BPMTK](activate_readonly_commands_for_bpmtk.html "ACTIVATE_READONLY_COMMANDS_FOR_BPMTK")  


Example 1:

```adoscript
{% raw %}

CC "UserMgt" REMOVE_SYSUSERS_FROM_GROUPS
        userids:"47111 47112" usergroups:"Group1\tGroup2" sep:"\t"
IF (ecode) {
    CC "AdoScript" ERRORBOX "Error!"
}

{% endraw %}
```
{: .line-numbers}

