---
layout: commandcall
category: CommandCall
title: "GET_SYSUSER_ID"
tags: 1.3 1.5
---

GET_SYSUSER_ID returns the ID of an ADOxx system user (userid).

# Syntax:  

```adoscript
{% raw %}
CC "UserMgt" GET_SYSUSER_ID user:strValue domain:strValue 
							logon-name-type:"samaccountname" | "principalname"
							[ ignore-case ]

# --> RESULT userid:intValue ecode:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`user`|strValue, user name|
|`domain`|strValue, domain name|
|`logon-name-type`|ogon-name type: "samaccountname" (user@domain) or	"principalname" (domain\user).|
|`ignore-case`|modifier, if given, case is ignored concerning the user name. This means that it does not matter if the user name is given in upper or lower case (or mixed).	If a user with such a name exists, its ID will be returned anyway.|

# Returns:  

|`ecode`|intValue, 0 (meaning success) or 1 (meaning error).|
|`userid`|intValue, ID of the specified ADOxx system user|

# Remarks:

Parameters

This command is available within both the ADOxx Development Toolkit and the ADOxx Modelling Toolkit. In the Modelling Toolkit only users that also have access to the Development Toolkit may call this command!

# See Also:  



Example:

