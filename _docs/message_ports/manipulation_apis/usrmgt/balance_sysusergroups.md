---
layout: commandcall
category: CommandCall
title: "BALANCE_SYSUSERGROUPS"
tags: 1.3 1.5
---

This component call balances an ADOxx system usergroup with operating system usergroups.

# Syntax:  

```adoscript
{% raw %}
CC "UserMgt" BALANCE_SYSUSERGROUPS	usergroup:strValue systemgroup:strValue
									domain:strValue library:strValue
									[ bpmtk:boolValue ] [ admtk:boolValue ]
									[ infotext:strValue ] 
									[ delete-type:"remove" | "delete" | "semi-delete" ] 
									[ sep:strValue ]

# --> RESULT ecode:intValue 
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`usergroup`|strValue, the name of the ADOxx user group to be balanced.|
|`systemgroup`|strValue, the names of the system user groups. If more are given, their names have to be separated by a specified separator. Specifying several system user groups means that all system users belonging to either of the groups are handled accordingly.|
|`domain`|strValue, the system domain name.|
|`library`|strValue, the name of the library where newly created users should be assigned to.|
|`bpmtk`|boolValue, has the user access on the ADOxx Modelling Toolkit? 0 = no, 1 = yes.|
|`admtk`|boolValue, has the user access on the ADOxx Development Toolkit? 0 = no, 1 = yes.|
|`infotext`|strValue, the user specific text.|
|`delete-type`|strValue, if the user is not contained in this usergroup any more "remove" = just unassign this user; "delete" = completely delete this user; "semi-delete" = move this user into the user trashcan (user can be found at "deleted users").|
|`sep`|strValue, This character is used to separate several system user groups (if more are to be balanced).|
Default value of the separator character is '\n'.

# Returns:  

ecode - intValue, Contains the error code or is 0 in case of success( 16 = Error enumerating domains; 17 = Error enumerating groups; 18 = Error enumerating users; 19 = Error reading the domains; 20 = Error - no domains; 21 = Error - domain not initialized; 22 = Error - user not found; 23 = Unspecific error.

# Remarks:

More than just one system user group can be specified in a single call of BALANCE_SYSUSERGROUPS.

This component call is only available in the ADOxx Development Toolkit.

# See Also:  



Example:

