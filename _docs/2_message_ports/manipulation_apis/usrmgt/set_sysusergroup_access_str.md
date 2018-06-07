---
layout: commandcall
category: CommandCall
title: "SET_SYSUSERGROUP_ACCESS_STR"
tags: 1.3 1.5
---

This AdoScript command sets the access string of an ADOxx system usergroup.

# Syntax:  

```adoscript
{% raw %}
CC "UserMgt" SET_SYSUSERGROUP_ACCESS_STR usergroup:strValue accessstr:strValue


# --> RESULT ecode:intValue

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`usergroup`|strValue, the name of the system usergroup|
|`accessstr`|strValue, the access string to be set|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|


# Remarks:

The syntax of the usergroup access string is not published. This command is only to get an access string from a certain system usergroup and assign those access rights to another ADOxx system usergroup.

This command is only available within ADOxx Development Toolkit

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "UserMgt" GET_SYSUSERGROUPS_ACCESS_STR usergroup:"SysAdmins"
IF (ecode = 0)
{
    CC "AdoScript" INFOBOX (accessstr)
}
ELSE
{
    CC "AdoScript" ERRORBOX "Could not get the access string of the usergroup SysAdmins!"
    EXIT
}

CC "UserMgt" SET_SYSUSERGROUP_ACCESS_STR usergroup:"Heroes" accessstr:(accessstr)
IF (ecode = 0)
{
    CC "AdoScript" INFOBOX ("Access string successfully set!")
}
ELSE
{
    CC "AdoScript" ERRORBOX "Could not set the access string!"
}

{% endraw %}
```
{: .line-numbers}

