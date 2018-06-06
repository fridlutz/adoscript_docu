---
layout: commandcall
category: CommandCall
title: "CREATE_USER"
tags: 1.3 1.5
---

CREATE_USER creates a new ADOxx user.

# Syntax:  

```adoscript
{% raw %}
CC "UserMgt" CREATE_USER	user:strValue password:strValue library:strValue 
							[ usergroups:strValue ] [ sep:strValue ]
							[ infotext:strValue ]
							[ bpmtk:intValue ] [ admtk:intValue ] [ sub-admin ].


# --> RESULT ecode:intValue userid:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`user`|strValue, the name of the user to be created|
|`password`|strValue, the password to login|
|`library`|strValue, the name of the application library the newly created user is assigned to|
|`usergroups`|strValue, the user will be assigned to one ore more usergroups. The user groups are specified as a string containing usergroup names, separated by the character passed with sep. The default value for sep is ";" (semicolon). However, it is recommended to use sep:"\t" (TAB).|
|`sep`|strValue, the user description string|
|`infotext`|strValue, the user description string|
|`bpmtk`|boolValue, Has the user access to the ADOxx Modelling Toolkit? 0 = no, 1 = yes.|
|`admtk`|boolValue, Has the user access to the ADOxx Development Toolkit? 0 = no, 1 = yes.|
|`sub-admin`|the user is a Sub-Administrator; This option has only an effect, if the user also has access to aadma!|

# Returns:  

|`ecode`|intValue, contains the error code or is 0 in case of success.|
|`userid`|strValue, the user id in case the user was created successfully (returned as string).|



# Remarks:

Attention!!! the type of userid is string (although it contains just one ID)!

Contrary to the UI (Development Toolkit) using this command is possible to create users containing invalid characters; e.g blanks at the begin and at the end - see the error messages ausmgt-22 and ausmgt-37. Such users cannot be the receiver of an ADOxx message, an error message will be shown if such a user is selected as recipient.

This command is available within both the ADOxx Development Toolkit and the ADOxx Modelling Toolkit. In the Modelling Toolkit only users that also have access to the Development Toolkit may call this command!

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "UserMgt" CREATE_USER
        user:"Smith" password:"OU812"
        library:"ADOxx-Standard-Anwendungsbibliothek 3.7"
        usergroups:"group1\tgroup2" sep:"\t"
        infotext:"Info..."
        admtk:0 bpmtk:1
IF (ecode) {
    CC "AdoScript" ERRORBOX "User could not be created!"
}

{% endraw %}
```
{: .line-numbers}

