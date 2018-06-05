---
layout: commandcall
category: CommandCall
title: "CHANGE_SYSUSER_SETTINGS"
tags: 1.3 1.5
---

This component call changes the settings of an ADOxx system user.

# Syntax:  

```adoscript
{% raw %}
CC "UserMgt" CHANGE_SYSUSER_SETTINGS User
									[ library:strValue ] [ infotext:strValue ]
									[ bpmtk:boolValue ] [ admtk:boolValue ]
									[ sub-admin:boolValue] .


User :		UserName | UserID .

UserName :	user:strValue domain:strValue [ ignore-case ].

UserID :	userid:intValue .

# --> RESULT ecode:intValue .

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`user`|strValue, The display name of the system user whose settings should be changed. If a user with such a name exists, its settings will be changed anyway.|
|`userid`|intValue, The ID of the system user|
|`domain`|strValue, The domain name of the system user.|
|`ignore-case`|modifier, if given, case is ignored concerning the user display name. This means that it does not matter if the user name is given in upper or lower case (or mixed).|
|`library`|strValu, The name of the application library the user is related to.|
|`infotext`|strValue, The user specific text.|
|`bpmtk`|boolValue, Has the user access to the ADOxx Modelling Toolkit? 0 = no, 1 = yes.|
|`admtk`|boolValue, Has the user access to the ADOxx Development Toolkit? 0 = no, 1 = yes.|
|`sub-admin`|boolValue, Is the system user a Sub-Administrator? 0 = no, 1 = yes.|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|

# Remarks:

The user is either specified by ID or by giving the display name and the domain name of the user.

This command is available within both the ADOxx Development Toolkit and the ADOxx Modelling Toolkit. In the Modelling Toolkit only users that also have access to the Development Toolkit may call this command!

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "UserMgt" CHANGE_SYSUSER_SETTINGS
      user:"Superman" domain:"SuperDomain"
      library:"ADOxx-Standard-Anwendungsbibliothek 4.0"
      infotext:"New text" bpmtk:1 admtk:0
IF (ecode = 0) {
    CC "AdoScript" INFOBOX "Usersettings changed successfully!"
} ELSE {
    CC "AdoScript" ERRORBOX "Could not apply the usersettings."
}

{% endraw %}
```
{: .line-numbers}

