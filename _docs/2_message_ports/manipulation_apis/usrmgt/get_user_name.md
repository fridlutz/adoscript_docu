---
layout: commandcall
category: CommandCall
title: "GET_USER_NAME"
tags: 1.3 1.5
---

GET_USER_NAME returns the name of a user with a certain ID.

# Syntax:  

```adoscript
{% raw %}
CC "UserMgt" GET_USER_NAME userid:intValue 

# --> RESULT username:strValue ecode:intValue 
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`userid`|intValue, ID of an ADOxx system user|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`username`|strValue, name of the specified user|

# Remarks:

This command is actually meant for ADOxx users. When you call this command with the ID of a system user, a GUID string is returned as user name. The UI user name can be determined with the command GET_SYSUSER_INFO, as shown in the example below.

This command is available within both the ADOxx Development Toolkit and the ADOxx Modelling Toolkit.

# See Also:  

[GET_SYSUSER_INFO](get_sysuser_info.html "GET_SYSUSER_INFO")  


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

