---
layout: commandcall
category: CommandCall
title: "GET_USER_PREFERENCES"
tags: 1.3 1.5
---

GET_USER_PREFERENCES returns the value of the specified user preference.

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_USER_PREFERENCES preference:strValue

#--> RESULT ecode:intValue val:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

preference - strValue, a preference string that may have one of the following values "GPM_WB" - docking windows settings; "GPM_WW" - Work window settings; "DOCUMENTATION SETTINGS" - documentation settings; "REFERENCEPROFILE - Default" - Default reference settings, used by the "open model" routine, e.g. from the Explorer; "REFERENCEPROFILE - Docu" - "Docu" reference settings; "ACFILTER SETTINGS" - Settings for the "attribute and class filter"; "MESSAGING" - settings for messaging.

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`val`|strValue, contains the returned LEO string.|

# Remarks:



# See Also:  

[SET_USER_PREFERENCES](set_user_preferences.html "SET_USER_PREFERENCES")  


Example 1:

Get the documentation user preferences  
```adoscript
{% raw %}

# get the documentation user preferences
CC "Core" GET_USER_PREFERENCES preference:"DOCUMENTATION SETTINGS"
# show the content
CC "AdoScript" INFOBOX (val)

{% endraw %}
```
{: .line-numbers}

