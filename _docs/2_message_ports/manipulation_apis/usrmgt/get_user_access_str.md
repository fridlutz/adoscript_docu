---
layout: commandcall
category: CommandCall
title: "GET_USER_ACCESS_STR"
tags: 1.3 1.5
---



# Syntax:  

```adoscript
{% raw %}
   CC "UserMgt"	 GET_USER_ACCESS_STR user:strValue


-->	RESULT ecode:intValue accessstr:strValue

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`user`|strValue, the name of the user|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`accessstr`|strValue, contains the current access rights of this user.|

# Remarks:

This AdoScript command returns the current access string of an ADOxx user.

The syntax of the user access string is not published. This command is only to get an access string from a certain user and assign those access rights to another ADOxx user.

This command is available within both the ADOxx Development Toolkit and the ADOxx Modelling Toolkit. In the Modelling Toolkit only users that also have access to the Development Toolkit may call this command!  
With the messageport command ACTIVATE_READONLY_COMMANDS_FOR_BPMTK  this behaviour can be changed.

# See Also:  

[ACTIVATE_READONLY_COMMANDS_FOR_BPMTK](activate_readonly_commands_for_bpmtk.html "ACTIVATE_READONLY_COMMANDS_FOR_BPMTK")  


Example 1:

```adoscript
{% raw %}

CC "UserMgt" GET_USER_ACCESS_STR user:"Superman"
IF (ecode = 0)
{
    CC "AdoScript" INFOBOX (accessstr)
}
ELSE
{
    CC "AdoScript" ERRORBOX "Could not get user access string!"
    EXIT
}

CC "UserMgt" SET_USER_ACCESS_STR user:"Superwoman" accessstr:(accessstr)
IF (ecode = 0)
{
    CC "AdoScript" INFOBOX ("Superwoman has now the same rights as Superman!"
}
ELSE
{
    CC "AdoScript" ERRORBOX ("Could not assign the rights to Superwoman!"
}

{% endraw %}
```
{: .line-numbers}

