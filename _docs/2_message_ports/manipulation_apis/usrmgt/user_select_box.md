---
layout: commandcall
category: CommandCall
title: "USER_SELECT_BOX"
tags: 1.3 1.5
---

USER_SELECT_BOX shows a dialog where users/usergroups can be selected. A checkbox allows to toggle the view between all users and users that are currently logged in.

# Syntax:  

```adoscript
{% raw %}
CC "UserMgt" USER_SELECT_BOX	[ with-usergroups ]
								[ with-userdescriptions ]
								[ without-users ]
								[ usergroup-sel ]
								[ libname:strValue | libid:intValue ]
								[ title:strValue ]
								[ boxtext:strValue ]
								[ oktext:strValue ] .


# --> RESULT ecode:intValue endbutton:strValue usernames:strValue userids:strValue
               usergroupnames:strValue  usergroupids:strValue .

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`with-usergroups`|modifier, if specified, the users are displayed as child entries of usergroups (where they are attached). Additionally a checkbox is displayed at the bottom of the dialog that allows to switch between a flat list displaying only the users and the hierarchical display with the usergroups.|
|`with-userdescriptions`|modifier, if specified, user specific information can be shown (by using an according command from the popup menu). If libname or libid is specified it acts as a filter for displayed users: Only users that have the given application library attached will be displayed in the list.|
|`without-users`|modifier, if specified, a flat list of usergroups is displayed.|
|`usergroup-sel`|modifier, if specified, usergroups can also be selected (as default the user select box only allows the selection of users).|
|`libname`|strValue|
|`libid`|intValue|
|`title`|strValue, the dialog title|
|`boxtext`|strValue, the label of the treelistbox displaying the users|
|`oktext`|strValue, the label of the ok-button|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`endbutton`|strValue, specifies which button has been pushed to close the dialog. If the user pushes the "OK" button, it is set to "ok". If he pushes "Cancel" it is set to "cancel".|
|`usernames`|strValue, contains the names of the selected users, separated by \n characters.|
|`userids`|strValue, contains the IDs of the selected users, separated by blanks.|
|`usergroupnames`|strValue, contains the names of the selected usergroups, separated by \n characters.|
|`usergroupids`|strValue, contains the IDs of the selected usergroups, separated by blanks.|

# Remarks:

If without-users and with-usergroups is specified, usergroup-sel is not necessary!

As this "double-name" feature only applies to system users, you should always use  
&gt;token(username, 0, "\t")  
to fetch the display name of the user (independently if it is a system user or not)!

If several users or usergroups have been selected, the position of the names and IDs in the strings usernames/userids resp. usergroupnames/usergroupids correspond, i.e. the first entry in the name list is the name of the object with the first ID in the corresponding ID list, etc.

This command is available within both the ADOxx Development Toolkit and the ADOxx Modelling Toolkit. In the Modelling Toolkit only users that also have access to the Development Toolkit may call this command!  
With the messageport command ACTIVATE_READONLY_COMMANDS_FOR_BPMTK  this behaviour can be changed.

# See Also:  

[ACTIVATE_READONLY_COMMANDS_FOR_BPMTK](activate_readonly_commands_for_bpmtk.html "ACTIVATE_READONLY_COMMANDS_FOR_BPMTK")  


Example 1:

```adoscript
{% raw %}

...
CC "UserMgt" USER_SELECT_BOX
        oktext:"Hit Me!" boxtext:"Please select users:"
        title:"USER_SELECTBOX example"
        with-usergroups

{% endraw %}
```
{: .line-numbers}

![](/images/USER_SELECT_BOX.png)
