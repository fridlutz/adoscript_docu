---
layout: commandcall
category: CommandCall
title: "SET_USER_PREFERENCES"
tags: 1.3 1.5
---

SET_USER_PREFERENCES changes the value of the specified user preference. This command directly accesses the database.

# Syntax:  

```adoscript
{% raw %}
CC "Core" SET_USER_PREFERENCES preference:strValue val:strValue

#-->RESULT ecode:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

preference - strValue, a preference string that may have one of the following values "GPM_WB" - docking windows settings; "GPM_WW" - Work window settings; "DOCUMENTATION SETTINGS" - documentation settings; "REFERENCEPROFILE - Default" - Default reference settings, used by the "open model" routine, e.g. from the Explorer; "REFERENCEPROFILE - Docu" - "Docu" reference settings; "ACFILTER SETTINGS" - Settings for the "attribute and class filter"; "MESSAGING" - settings for messaging.
|`val`|strValue, contains the "preference" value; it must be valid LEO and ending with a newline character.|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|

# Remarks:



# See Also:  

[GET_USER_PREFERENCES](get_user_preferences.html "GET_USER_PREFERENCES")  


Example 1:

Set the documentation user preferences  
```adoscript
{% raw %}

# get the documentation user preferences
CC "Core" GET_USER_PREFERENCES preference:"DOCUMENTATION SETTINGS"
# set the preferences as read from the DB
CC "Core" SET_USER_PREFERENCES preference:"DOCUMENTATION SETTINGS" val:(val)

{% endraw %}
```
{: .line-numbers}
