---
layout: commandcall
category: CommandCall
title: "DELETE_USERS"
tags: 1.3 1.5
---

DELETE_USERS deletes one or more ADOxx users.

# Syntax:  

```adoscript
{% raw %}
CC "UserMgt" DELETE_USERS users:strValue [ sep:strValue ]

# --> RESULT ecode:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`users`|strValue, specifies the names of one or more users to be deleted. The users are specified as a string containing user names, separated by the character passed with sep. The default value for sep is ";" (semicolon). However, it is recommended to use sep:"\t" (TAB).|
|`sep`|strValue|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|

# Remarks:

This command is only available within the ADOxx Development Toolkit.


# See Also:  



Example 1:

```adoscript
{% raw %}

CC "UserMgt" DELETE_USERS users:"Peter\tPaul\tMary" sep:"\t"
IF (ecode) {
    CC "AdoScript" ERRORBOX "Users could not be deleted!"
}

{% endraw %}
```
{: .line-numbers}


