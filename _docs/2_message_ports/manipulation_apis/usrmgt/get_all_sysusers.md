---
layout: commandcall
category: CommandCall
title: "GET_ALL_SYSUSERS"
tags: 1.3 1.5
---

GET_ALL_SYSUSERS returns the names of all ADOxx system users.

# Syntax:  

```adoscript
{% raw %}
CC "UserMgt" GET_ALL_SYSUSERS .


# --> RESULT users:strValue ecode:intValue .

{% endraw %}
```
{: .line-numbers}

# Parameters:  

none

# Returns:  

|`ecode`|intValue, 0 (meaning success) or 1 (meaning error).|
|`users`|strValue, containins system user name items separated by "\n" (NEWLINE). Each system user name item consists of three parts: the actual user name, the related domain name and the related logon name type. These three parts are separated by "\t" (TAB). The logon name type is either "samaccountname" (user@domain) or "principalname" (domain\user).|

# Remarks:

This command is available within both the ADOxx Development Toolkit and the ADOxx Modelling Toolkit.

# See Also:  



Example:

