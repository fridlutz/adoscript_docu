---
layout: commandcall
category: CommandCall
title: "GET_ALL_SYSUSERGROUPS"
tags: 1.3 1.5
---

GET_ALL_SYSUSERGROUPS returns all ADOxx system user groups.

# Syntax:  

```adoscript
{% raw %}
CC "UserMgt" GET_ALL_SYSUSERGROUPS [ sep:strValue ]

# --> RESULT ecode:intValue usergroups:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`sep`|strValue|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`usergroups`|strValue, contains the names of the system user groups separated by the character passed with sep. The default value for sep is ";" (semicolon). However, it is recommended to use sep:"\t" (TAB).|

# Remarks:

This command is available within both the ADOxx Development Toolkit and the ADOxx Modelling Toolkit. In the Modelling Toolkit only users that also have access to the Development Toolkit may call this command! With the command ACTIVATE_READONLY_COMMANDS_FOR_BPMTK this behaviour can be changed.

# See Also:  

[ACTIVATE_READONLY_COMMANDS_FOR_BPMTK](activate_readonly_commands_for_bpmtk.html "ACTIVATE_READONLY_COMMANDS_FOR_BPMTK")  


Example 1:

```adoscript
{% raw %}

CC "UserMgt" GET_ALL_SYSUSERGROUPS sep:"\t"
IF (ecode) {
    CC "AdoScript" ERRORBOX "Could not get system user groups!"
}

{% endraw %}
```
{: .line-numbers}

