---
layout: commandcall
category: CommandCall
title: "MESSAGE_SEARCH"
tags: 1.3 1.5
---

The command MESSAGE_SEARCH searches all messages for the given expression.

# Syntax:  

```adoscript
{% raw %}
CC "Application" MESSAGE_SEARCH strValue

#--> RESULT ecode:intValue messageids:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`<main_parameter>`|strValue|

# Returns:  

|`ecode`|intValue, contains the error code or is 0 in case of success.|
|`messageids`|strValue, contains a list with the IDs of the found messages.|

# Remarks:

The string is interpreted as a regular expression and is searched in the DATA part of its message.

# See Also:  

[MESSAGE_SEND](message_send.html "MESSAGE_SEND")  


Example 1:

Search all messages in the DB for the string "Brief schreiben" appearing at the start of the DATA part of the message.  
```adoscript
{% raw %}

CC "Application" MESSAGE_SEARCH "^Brief schreiben"
IF (ecode = 0)
{
  SET n: (tokcnt (messageids, " "))
  IF (n = 0)
  {
    CC "AdoScript" INFOBOX "No messages found!"
  }
  ELSIF (n = 1)
  {
    CC "AdoScript" INFOBOX ("There is one message fulfilling the entered search criteria:\n\n" + messageids)
  }
  ELSE
  {
    SET str:""
    FOR id in:(messageids)
    {
      SET str: (str + "\n" + id)
    }
    CC "AdoScript" INFOBOX ("There are " + STR n + " messages fulfilling the entered search criteria:\n" + str)
  }
}
ELSE
{
  CC "AdoScript" ERRORBOX "An error occured while searching messages!"
}

{% endraw %}
```
{: .line-numbers}

