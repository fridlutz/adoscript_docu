---
layout: commandcall
category: CommandCall
title: "MESSAGE_DELETE"
tags: 1.3 1.5
---

The command MESSAGE_DELETE deletes the message with the given ID from the DB.

# Syntax:  

```adoscript
{% raw %}
CC "Application" MESSAGE_DELETE messageid:intValue [ userid:intValue | username:strValue]

#--> RESULT ecode:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`messageid`|intValue, the ID of the message|
|`userid`|intValue, the ID of the user|
|`username`|strValue, the name of the user|

# Returns:  

ecode - intValue, 0 if the message was deleted successfully, 1 if wrong parameters have been passed - message was not deleted, 2 if no valid users have been passed - message was not deleted, 3 if an error occured while deleting the message (although the parameters seemed OK)

# Remarks:

If a message was sent to n recipients, there will be n rows in the DB. If MESSAGE_DELETE is called without any userid/username, all n rows will be deleted. If a userid/username is given, just this one row is deleted.

# See Also:  



Example 1:

Delete all messages containing the string "Write letter" at the start of the DATA part of the message.

```adoscript
{% raw %}

CC "Application" MESSAGE_SEARCH "Write letter"
IF (ecode = 0)
{
  SET n: (tokcnt (messageids, " "))
  IF (n = 0)
  {
    CC "AdoScript" INFOBOX "No messages found!"
  }
  ELSE
  {
    FOR id in:(messageids)
    {
      CC "Application" MESSAGE_DELETE messageid:(VAL id)
    }
  }
}
ELSE
{
  CC "AdoScript" ERRORBOX "An error occured while searching messages!"
}

{% endraw %}
```
{: .line-numbers}

