---
layout: commandcall
category: CommandCall
title: "MARK_MESSAGES_UNREAD"
tags: 1.3 1.5
---

MARK_MESSAGES_UNREAD marks the given messages for the given user (user is recipient) as unread.

# Syntax:  

```adoscript
{% raw %}
CC "Application" MARK_MESSAGES_UNREAD messageids:strValue userid:intValue

#--> RESULT ecode:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`messageids`|strValue, a string containing the IDs of the messages (blank separated).|
|`userid`|intValue, is the ID of the recipient of the messages.|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|

# Remarks:

This command works both for normal and for system users.

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "UserMgt" GET_USER_ID_OF_CURRENT_USER
CC "Application" MESSAGE_SEARCH "Text"
CC "Application" MARK_MESSAGES_UNREAD messageids:(messageids) userid:(userid)

{% endraw %}
```
{: .line-numbers}

