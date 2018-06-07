---
layout: commandcall
category: CommandCall
title: "UDL_EXPORT"
tags: 1.3 1.5
---

UDL_EXPORT is an AdoScript command available through the ImportExport messageport within the ADOxx Development Toolkit.

# Syntax:  

```adoscript
{% raw %}
CC "ImportExport" UDL_EXPORT file:fileName 
				( userids:strValue [ usergroupids:strValue ] | usergroupids:strValue [ userids:strValue ] )
				[ with-users:(0|1) ] [ with-usergroups:(0|1) ] [ with-password:(0|1) ] 
				[ overwrite-file:(0|1) ]  [ silent ].

#--> RESULT ecode:intValue 
			errtext:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`file`|fileName, the path to the target file.|
|`userids`|strValue, a space-separated string holding the IDs of users to be exported.|
|`usergroupids`|strValue, a space-separated string holding the IDs of usergroups to be exported.|
|`with-users`|(0|1), flag determining whether user data is to be exported (default value is 1).|
|`with-usergroups`|(0|1), flag determining whether usergroup data is to be exported (default value is 0).|
|`with-password`|(0|1), flag determining whether user passwords are to be exported (default value is 0).|
|`overwrite-file`|(0|1), flag determining whether an existing file is to be overwritten (default value is 0).|
|`silent`|modifier, flag determining whether all error- and success-messages are supressed  (default value is "Not suppressed").|

# Returns:  

|`ecode`|intValue, 0|1|
|`errtext`|strValue contains an error text that can be displayed.|

# Remarks:

According to its dialog-based counterpart it performs the export of ADOxx users to an UDL file, allowing for various options to control the export process.

Pssible **errtext** values are  
* Invalid Parameters
* File exists
* File cannot be created
* File cannot be overwritten
* Directory has been passed
* No valid IDs
* UDL export successfull
* UDL export failed

# See Also:  

[UDL_IMPORT](udl_import.html "UDL_IMPORT")  


Example 1:

```adoscript
{% raw %}

CC "AdoScript" FILE_DIALOG saveas filter1:"UDL Files" type1:"**.udl"
IF (endbutton != "ok")
{
   EXIT
}

CC "UserMgt" GET_USERID user:"Superman"
SET sUserIDs: (STR userid)
CC "UserMgt" GET_USERID user:"Supergirl"
SET sUserIDs: (sUserIDs + " " + (STR userid))

CC "UserMgt" GET_USERGROUPID usergroup:"Beatles"
SET sUserGroupIDs: (STR usergroupid)

CC "ImportExport" UDL_EXPORT file:(path) userids:(sUserIDs) usergroupids:(sUserGroupIDs) with-usergroups:1 with-password:1 overwrite-file:1

IF (ecode = 0)
{
   CC "AdoScript" INFOBOX (errtext) title:"UDL Export"
}
ELSE
{
   CC "AdoScript" ERRORBOX (errtext) title:"UDL Export"
}

{% endraw %}
```
{: .line-numbers}

First the file dialog is opened and the user enters an UDL file. Then the users Superman and Supergirl are exported to this file. An Info- or Errorbox reports whether the export has succeeded.

