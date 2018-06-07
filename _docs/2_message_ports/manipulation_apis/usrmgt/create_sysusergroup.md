---
layout: commandcall
category: CommandCall
title: "CREATE_SYSUSERGROUP"
tags: 1.3 1.5
---

This AdoScript command creates a new ADOxx system usergroup.

# Syntax:  

```adoscript
{% raw %}
CC "UserMgt" CREATE_SYSUSERGROUP usergroup:strValue [ userids:strValue]  [ global ]

# --> RESULT ecode:intValue usergroupid:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`usergroup`|strValue, the name of the usergroup to be created|
|`userids`|strValue, the IDs of system users to be assigned to this newly created usergroup (separated by blanks).|
|`global`|modifier, if the new system user group is a global user group. If this is omitted, the system user group will be created as a local user group.|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`usergroupid`|intValue, the id of the usergroup if the function succeeded.|

# Remarks:

This command is only available within ADOxx Development Toolkit

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "UserMgt" CREATE_SYSUSERGROUP usergroup:"Heroes" userids:"47111 47112"
IF (ecode = 0)
{
    CC "AdoScript" INFOBOX (usergroupid)
}
ELSE
{
    CC "AdoScript" ERRORBOX "Usergroup Heroes could not be created!"
}

{% endraw %}
```
{: .line-numbers}

