---
layout: commandcall
category: CommandCall
title: "SET_SYSUSER_ACCESS_STR"
tags: 1.3 1.5
---

This AdoScript command changes the access string of an ADOxx system user.

# Syntax:  

```adoscript
{% raw %}
    CC "UserMgt" SET_SYSUSER_ACCESS_STR	user:strValuedomain:strValue[ ignore-case ] | userid:intValue) accessstr:strValue


# --> RESULT ecode:intValue

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`user`|strValue, the display name of the user|
|`domain`|strValue, the display name of the domain of the user|
|`ignore-case`|modifier, if given, case is ignored concerning the user display name. This means that it does not matter if the user name is given in upper or lower case (or mixed). If a user with such a name exists, its access string will be set anyway.|
|`userid`|intValue, the ID of the system user.|
|`accessstr`|strValue, the access string which should be set|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|


# Remarks:

The syntax of the user access string is not published. This command is only to get an access string from a certain user and assign those access rights to another ADOxx user.

This command is available within both the ADOxx Development Toolkit and the ADOxx Modelling Toolkit. In the Modelling Toolkit only users that also have access to the Development Toolkit may call this command!

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "UserMgt" GET_SYSUSER_ACCESS_STR user:"Superman" domain:"Superdomain"
IF (ecode = 0)
{
    CC "AdoScript" INFOBOX (accessstr)
}
ELSE
{
    CC "AdoScript" ERRORBOX "Could not get user access string!"
    EXIT
}

CC "UserMgt" SET_SYSUSER_ACCESS_STR user:"Superwoman" domain:"Superdomain" accessstr:(accessstr)
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

