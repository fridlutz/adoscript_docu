---
layout: commandcall
category: CommandCall
title: "MESSAGE_SEND"
tags: 1.3 1.5
---

The command MESSAGE_SEND sends a message.

# Syntax:  

```adoscript
{% raw %}
CC "Application" MESSAGE_SEND 	(usernames:strValue | userids:strValue) 
								[ ( sendername:strValue | senderid:intValue ) ] 
								subject:strValue
								message:strValue 
								[ express: 0|1 ]

#--> RESULT ecode:intValue messageid:intValue .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`usernames`|strValue, semicolon separated list of usernames in a string.|
|`userids`|strValue, space separated list of numeric user-ids in a string.|
|`sendername`|strValue, if given, this user will appear as sender of the message.|
|`senderid`|intValue, if given, this user will appear as sender of the message.|
|`subject`|strValue, subject of the message.|
|`message`|strValue, content of the message.|
|`express`|0|1|

# Returns:  

ecode - intValue, 0 in case of success, 1 if wrong parameters have been passed - no message sent, 2 if no valid users have been passed - no message sent, other value if an error occured while sending the message.
|`messageid`|intValue, holds its database id, otherwise it is set to -1.|

# Remarks:

If there are invalid userids or usernames they are ignored and the message is sent to the valid ones only.

By default, the sender of the message is the current user, i.e. the user executing the command.

Since ADOxx version 1.3UL1 the message body can either be plain text or a LEO coded hypertext. Within such a hypertext, text parts, hyperlinks and linebreaks can be specified. The element HYPERLINK represents a hyperlink, whose text is set in the attribute text, the attribute href is supposed to be an AdoScript that is executed, when the according hyperlink is clicked in the message view. The element DATA allows to set a message specific string which will not be displayed when the message is read, but which can be searched for and used to persist additional message relevant information. The string set there will also be available to those AdoScripts that are executed if a hyperlink is clicked.

```adoscript
{% raw %}
HyperText :	HYPERTEXT { Text | Hyperlink | Linebreak | Data }

Text :	TEXT strValue

Hyperlink :	HYPERLINK text:strValue href:strValue

Linebreak :	LINEBREAK

Data :	DATA strValue
{% endraw %}
```
{: .line-numbers}

# See Also:  



Example 1:

This AdoScript sends an express message to the valid users among userid 11002 and usernames Supergirl and Superman or exits with an ecode &gt; 0 if none of them is valid.  
```adoscript
{% raw %}

SET nUserid:11002
SET sUsernames:"Supergirl;Superman"
CC "Application" MESSAGE_SEND userids:(STR nUserid) usernames:(sUsernames) 
							subject:"Test message" 
							message:"This is urgent - so read it now!" 
							express:1
IF (ecode = 0) {
    SET sInfoText: "Message was sent successfully.\nMessage ID: "
    SET sInfoText: (sInfoText + (STR messageid) + ".")
    CC "AdoScript" INFOBOX (sInfoText)
} ELSE {
    CC "AdoScript" ERRORBOX ("An error occured while trying to send message!\necode: " + (STR ecode))
}

{% endraw %}
```
{: .line-numbers}

