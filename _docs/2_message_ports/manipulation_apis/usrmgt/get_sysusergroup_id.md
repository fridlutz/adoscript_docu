---
layout: commandcall
category: CommandCall
title: "GET_SYSUSERGROUP_ID"
tags: 1.3 1.5
---

This AdoScript command returns the ID of an ADOxx system usergroup.

# Syntax:  

```adoscript
{% raw %}
CC "UserMgt" GET_SYSUSERGROUP_ID usergroup:strValue

# --> RESULT ecode:intValue usergroupid:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`usergroup`|strValue, the usergroup name which ID should be returned|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`usergroupid`|intValue, the id of the usergroup|

# Remarks:

This command is available within both the ADOxx Development Toolkit and the ADOxx Modelling Toolkit. In the Modelling Toolkit only users that also have access to the Development Toolkit may call this command!  
With the messageport command ACTIVATE_READONLY_COMMANDS_FOR_BPMTK  this behaviour can be changed.

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "UserMgt" GET_SYSUSERGROUP_ID usergroup:"Beatles"
IF (ecode = 0)
{
    CC "AdoScript" INFOBOX (usergroupid)
}
ELSE
{
    CC "AdoScript" ERRORBOX "The Beatles' ID could not be retreived!"
}

{% endraw %}
```
{: .line-numbers}

