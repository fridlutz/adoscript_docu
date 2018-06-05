---
layout: commandcall
category: CommandCall
title: "GET_CURRENT_USER_ID"
tags: 1.3 1.5
---

GET_CURRENT_USER_ID returns the ID and the type of the current user.

# Syntax:  

```adoscript
{% raw %}
CC "UserMgt" GET_CURRENT_USER_ID

# --> RESULT userid:intValue usertype:UserType eCode:intValue .
UserType :   "system" | "internal" .

{% endraw %}
```
{: .line-numbers}

# Parameters:  

none

# Returns:  

|`ecode`|intValue, 0 (meaning success) or 1 (meaning error).|
|`userid`|intValue, ID of the current user|
|`usertype`|strValue, Type of the current user; "system" (system user) or "internal" (ADOxx user).|

# Remarks:

This command is available within both the ADOxx Development Toolkit and the ADOxx Modelling Toolkit.

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "UserMgt" GET_CURRENT_USER_ID
IF (usertype = "system") {
    CC "UserMgt" GET_SYSUSER_INFO userid:(userid)
    SET n:(cond(?logon-name-type = "samaccountname",
                username + "@" + domain,
                domain + "\\" + username))
} ELSE {
    CC "UserMgt" GET_USER_NAME userid:(userid)
    SET n:(username)
}
CC "AdoScript" INFOBOX ("Hello " + n + "!")

{% endraw %}
```
{: .line-numbers}

