---
layout: commandcall
category: CommandCall
title: "CHANGE_USER_SETTINGS"
tags: 1.3 1.5
---

This component call changes the settings of an ADOxx user.

# Syntax:  

```adoscript
{% raw %}
CC "UserMgt" CHANGE_USER_SETTINGS user:strValue [ password:strValue ]
								  [ library:strValue ] [ infotext:strValue ]
								  [ bpmtk:boolValue ] [ admtk:boolValue ]
								  [ sub-admin:boolValue]

# --> RESULT ecode:intValue 
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`user`|strValue, The name of the user whose settings should be changed.|
|`password`|strValue, The user's login password.|
|`library`|strValue, The name of the application library the user is related to.|
|`infotext`|strValue, The user specific text.|
|`bpmtk`|boolValue, Has the user access to the ADOxx Modelling Toolkit? 0 = no, 1 = yes.|
|`admtk`|boolValue, Has the user access to the ADOxx Development Toolkit? 0 = no, 1 = yes.|
|`sub-admin`|boolValue, Is the system user a Sub-Administrator? 0 = no, 1 = yes.|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|


# Remarks:

This command is available within both the ADOxx Development Toolkit and the ADOxx Modelling Toolkit. In the Modelling Toolkit only users that also have access to the Development Toolkit may call this command!

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "UserMgt" CHANGE_USER_SETTINGS
      user:"Superman" password:"superwomen"
      library:"ADOxx-Standard-Library"
      infotext:"New text" bpmtk:1 admtk:0
IF (ecode = 0) {
    CC "AdoScript" INFOBOX "Usersettings changed successfully!"
} ELSE {
    CC "AdoScript" ERRORBOX "Could not apply  the usersettings."
}

{% endraw %}
```
{: .line-numbers}

