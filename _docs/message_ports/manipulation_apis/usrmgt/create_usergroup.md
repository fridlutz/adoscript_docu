---
layout: commandcall
category: CommandCall
title: "CREATE_USERGROUP"
tags: 1.3 1.5
---

CREATE_USERGROUP creates a new ADOxx usergroup.

# Syntax:  

```adoscript
{% raw %}
CC "UserMgt" CREATE_USERGROUP usergroup:strValue [ users:strValue ] [ sep:strValue ]
							[ global ]

# --> RESULT ecode:intValue usergroupid:ID .

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`usergroup`|strValue, the name of the usergroup to be created|
|`users`|strValue, the users to be assigned to  this newly created usergroup. The users are specified as a string containing user names, separated by the character passed with sep. The default value for sep is ";" (semicolon). However, it is recommended to use sep:"\t" (TAB).|
|`sep`|strValue,|
|`global`|modifier, specifies if the new user group is a global user group. If this is omitted, the user group will be created as a local user group.|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`usergroupid`|intValue, the id of the usergroup|

# Remarks:

The returned ecode is 0 if the command has been executed successfully. If there was an error or if the usergroup already exists, a nonzero value is returned.

This command is only available in the ADOxx Development Toolkit.

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "UserMgt" CREATE_USERGROUP
        usergroup:"My Group" users:"Peter\tPaul\tMary" sep:"\t"
IF (ecode) {
    CC "AdoScript" ERRORBOX "User group could not be created!"
}

{% endraw %}
```
{: .line-numbers}

