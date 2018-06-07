---
layout: commandcall
category: CommandCall
title: "DELETE_SYSUSERS"
tags: 1.3 1.5
---

This AdoScript command deletes one ore more ADOxx system users.

# Syntax:  

```adoscript
{% raw %}
CC "UserMgt" DELETE_SYSUSERS userids:intValue[;intValue(...)]

# --> RESULT ecode:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`userids`|intValue, one or more system user ids of ADOxx system users to be created.|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|


# Remarks:

This command is only available within ADOxx Development Toolkit

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "UserMgt" GET_SYSUSER_ID user:"user1" domain:"system" logon-name-type:"samaccountname"
IF (ecode = 0)
{
    CC "AdoScript" INFOBOX (userid)
}
ELSE
{
    CC "AdoScript" ERRORBOX "Failed to get the user id!"
    EXIT
}

CC "UserMgt" DELETE_SYSUSERS userids:(userid)
IF (ecode = 0)
{
    CC "AdoScript" INFOBOX "User \"user1\" successfully deleted!"
}
ELSE
{
    CC "AdoScript" ERRORBOX "Could not delete \"user1\"."
}

{% endraw %}
```
{: .line-numbers}

