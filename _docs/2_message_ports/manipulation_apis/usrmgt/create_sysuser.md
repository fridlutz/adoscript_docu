---
layout: commandcall
category: CommandCall
title: "CREATE_SYSUSER"
tags: 1.3 1.5
---

CREATE_SYSUSER creates a new ADOxx system user.

# Syntax:  

```adoscript
{% raw %}
CC "UserMgt" CREATE_SYSUSER	username:strValue domain:strValue library:strValue 
							[ usergroups:strValue ] [ sep:strValue ]
							[ infotext:strValue ]
							[ bpmtk:intValue ] [ admtk:intValue ] [ sub-admin ]
							[ no-validate ] [ useruuid:strValue ] [ domainuuid:strValue].


# --> RESULT ecode:intValue userid:strValue .
        -- Attention: the type of userid is string (although it contains just one ID)! 

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`username`|strValue, the (display) name of the user to be created|
|`domain`|strValue, the (display) name of the domain of the user|
|`library`|strValue, the name of the application library the newly created user is assigned to|
|`usergroups`|strValue, the user will be assigned to one ore more usergroups. The user groups are specified as a string containing usergroup names, separated by the character passed with sep. The default value for sep is ";" (semicolon). However, it is recommended to use sep:"\t" (TAB).|
|`sep`|strValue,|
|`infotext`|strValue, the user description string|
|`bpmtk`|boolValue, Has the user access to the ADOxx Modelling Toolkit? 0 = no, 1 = yes.|
|`admtk`|boolValue, Has the user access to the ADOxx Development Toolkit? 0 = no, 1 = yes.|
|`sub-admin`|boolValue, Is the system user a Sub-Administrator? 0 = no, 1 = yes.|
|`no-validate`|modifier, if given, the existance of the user in the system is not checked! In that case, also the parameters useruuid and domainuuid have to be specified (in case of validation these parameters would have been fetched from the provider). The parameter useruuid has to contain the UUID of the user in the system and domainuuid has to contain the UUID of the domain. Note that these strings must only contain the 32 hexadecimal digits of the UUID, no '{' or '-' characters!|
|`useruuid`|strValue|
|`domainuuid`|strValue|

# Returns:  

|`ecode`|intValue, is 0 in case of success or an error code; 1 = missing or wrong parameters, 2 = SSO is not active (so sys users can not be created), 3 = sys user does not exist in the given domain, 4 = sys user already exists in ADOxx DB, 5 =other (e.g. general) error|
|`errtext`|strValue, contains a textual representation of the ecode|

# Remarks:

If the parameter no-validate is given, the existance of the user in the system is not checked!

This no-validate version of the command only works for provider Active Directory, WinNT is not supported!  
Note also that useruuid and domainuuid will be ignored, if no-validate is missing.

This command is available within both the ADOxx Development Toolkit and the ADOxx Modelling Toolkit. In the Modelling Toolkit only users that also have access to the Development Toolkit may call this command!

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "UserMgt" CREATE_SYSUSER
        username:"Smith" domain:"mydomain"
        library:"ADOxx-BPMS-Anwendungsbibliothek 3.9"
        usergroups:"group1\tgroup2" sep:"\t"
        infotext:"Info..."
        admtk:0 bpmtk:1
IF (ecode) {
    CC "AdoScript" ERRORBOX "System user could not be created!"
}

{% endraw %}
```
{: .line-numbers}

