---
layout: commandcall
category: CommandCall
title: "UDL_IMPORT"
tags: 1.3 1.5
---

UDL_IMPORT is an AdoScript command available through the ImportExport messageport within the ADOxx Development Toolkit.

# Syntax:  

```adoscript
{% raw %}
CC "ImportExport" UDL_IMPORT file:fileName 
							[ existing-users: overwrite | rename | ignore | actualize ] 
							[ existing-usergroups: overwrite | adopt | rename | ignore | actualize ]
							[ existing-sysusers: overwrite | ignore | actualize ] 
							[ invalid-sysusers: ignore | convert ]
							[ from-libraryid:intValue  to-libraryid:intValue ]
							[ silent ] .

#-->	RESULT ecode:intValue 
		errtext:strValue .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`file`|fileName, the path to the file holding the user information. The .udl extension is not needed but is accepted.|
|`existing-users`|determines the reaction when importing a user who is already present in the database. If this option is not specified **ignore** is assumed.|
|`existing-usergroups`|determines the reaction when importing a usergroup that is already present in the database. If this option is not specified **adopt** is assumed.|
|`existing-sysusers`|determines the reaction when importing a system user who is already present in the database. If this option is not specified **ignore** is assumed.|
|`invalid-sysusers`|determines the reaction when encountering a system user who is not member of the user domain structure or when importing system users without having Single-Sign-On enabled. When convert is passed, the users are converted into Adonis-internal users. If this option is not specified **ignore** is assumed.|
|`from-libraryid`|intValue, during the import of user data the assignment of the application library can be changed. With this option the original library is given.|
|`to-libraryid`|intValue, the new library that is assigned to those users who are being imported and have from-lybraryid assigned within the UDL file.|
|`silent`|modifier, if given, all error- and success-messages are supressed.|

# Returns:  

|`ecode`|intValue, specifies whether the udl file was imported successfully or not. ecode is set to 0 if the import worked and to 1 if not.|
|`errtext`|strValue contains an error text that can be displayed.|

# Remarks:

According to its dialog-based counterpart it performs the import of ADOxx users from an UDL file, allowing for various options to control the import process.

Possible **errtext** values are

*Invalid Parameters
*File does not exist
*Invalid From-Library-ID
*Invalid To-Library-ID
*Could not initialize UDL import
*UDL import successfull
*UDL import failed

If a from-libraryid is given, a to-lybraryid is needed as well and vice versa.

# See Also:  

[UDL_EXPORT](udl_export.html "UDL_EXPORT")  


Example 1:

```adoscript
{% raw %}

CC "AdoScript" FILE_DIALOG open filter1:"UDL Files" type1:"**.udl"
IF (endbutton != "ok")
{
   EXIT
}

CC "ImportExport" UDL_IMPORT file:(path) existing-users:overwrite existing-usergroups:actualize invalid-sysusers:convert
IF (ecode = 0)
{
   CC "AdoScript" INFOBOX (errtext) title:"UDL Import"
}
ELSE
{
   CC "AdoScript" ERRORBOX (errtext) title:"UDL Import"
}

{% endraw %}
```
{: .line-numbers}

First the file dialog is opened and the user selects an UDL file. Then the selected file is imported overwriting existing users and updating existing usergroups. If the file contains system users who are not known to the user management, they are converted into ADOxx-internal users. An Info- or Errorbox reports whether the import has succeeded.

