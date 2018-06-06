---
layout: commandcall
category: CommandCall
title: "REMOVE_USERS_FROM_GROUPS"
tags: 1.3 1.5
---

REMOVE_USERS_FROM_GROUPS removes one or more ADOxx users from one or more user groups.

# Syntax:  

```adoscript
{% raw %}
CC "UserMgt" REMOVE_USERS_FROM_GROUPS 	users:strValue 
										usergroups:strValue
										[ sep:strValue ]

# --> RESULT ecode:intValue 
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`users`|strValue, string containing user names separated by the character passed with sep.|
|`usergroups`|strValue, one or more usergroup names, separated by the character passed with sep.|
The default value for sep is ";" (semicolon). However, it is recommended to use sep:"\t" (TAB).
|`sep`|strValue, default value for sep is ";" (semicolon). However, it is recommended to use sep:"\t" (TAB).|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|


# Remarks:

This command is available within both the ADOxx Development Toolkit and the ADOxx Modelling Toolkit. In the Modelling Toolkit only users that also have access to the Development Toolkit may call this command!  
However, with ACTIVATE_READONLY_COMMANDS_FOR_BPMTK this command can be activated also for non-admins (although it is actually not a readonly command).

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "UserMgt" REMOVE_USERS_FROM_GROUPS
        users:"Peter\tPaul\tMary"
        usergroups:"Group1\tGroup2"
        sep:"\t"
IF (ecode) {
    CC "AdoScript" ERRORBOX "Error!"
}

{% endraw %}
```
{: .line-numbers}

