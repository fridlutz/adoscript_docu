---
layout: commandcall
category: CommandCall
title: "GET_SYSUSER_INFO"
tags: 1.3 1.5
---

GET_SYSUSER_INFO returns data related to an ADOxx system user ID.

# Syntax:  

```adoscript
{% raw %}
CC "UserMgt" GET_SYSUSER_INFO userid:intValue

#--> RESULT username:strValue domain:strValue 
			logon-name-type:"samaccountname" | "principalname"
			ecode:intValue .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`userid`|intValue, ID of an ADOxx system user|

# Returns:  

|`ecode`|intValue, 0 (meaning success) or 1 (meaning error).|
|`username`|strValue, name of the specified user|
|`domain`|strValue, domain name related to the specified user|
|`logon-name-type`|"samaccountname" (username@domain) or "principalname" (domain\username)|

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

