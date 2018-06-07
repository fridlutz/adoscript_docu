---
layout: commandcall
category: CommandCall
title: "ADD_USERS_TO_GROUPS"
tags: 1.3 1.5
---

ADD_USERS_TO_GROUPS assigns one or more ADOxx users to one or more user groups.

# Syntax:  


```adoscript
{% raw %}
 CC "UserMgt" ADD_USERS_TO_GROUPS	users:strValue usergroups:strValue
									[ sep:strValue ] .

# --> RESULT ecode:intValue .

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`users`|strValue|
|`usergroups`|strValue|
|`sep`|strValue|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|


# Remarks:

users is a string containing user names, separated by the character passed with sep.  
usergroups is a string containing usergroup names, separated by the character passed with sep.  
The default value for sep is ";" (semicolon). However, it is recommended to use sep:"\t" (TAB).

The returned error code ecode is 0 if the command has been executed successfully. Any other value means that an error occured, e.g. if a specified user does not exist.

Note: This command is available within both the Development Toolkitand the Modelling Toolkit.  
In the Modelling Toolkit usually only users that also have access to the Development Toolkit can call this command. However, with ACTIVATE_READONLY_COMMANDS_FOR_BPMTK this command can be activated also for non-admins (although it is actually not a readonly command).

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "UserMgt" ADD_USERS_TO_GROUPS
    users:"Alpha\tBeta" usergroups:"Group1\tGroup2" sep:"\t"

{% endraw %}
```
{: .line-numbers}
assigns the users Alpha and Beta to the user groups Group1 and Group2.

