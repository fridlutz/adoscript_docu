---
layout: commandcall
category: CommandCall
title: "ACTIVATE_READONLY_COMMANDS_FOR_ADOxx ModellingTK"
tags: 1.3 1.5
---

ACTIVATE_READONLY_COMMANDS_FOR_ADOxx ModellingTK allows to activate commands which usually are restricted to users with administration rights only.

# Syntax:  

```adoscript
{% raw %}
CC "UserMgt" ACTIVATE_READONLY_COMMANDS_FOR_ADOxx ModellingTK yes | no

# --> RESULT ecode:intValue .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

none

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|

# Remarks:

As default several GET_** commands of the UserMgt messageport can in the ADOxx Modelling Toolkit only be called by users with administration rights.  
Calling the command with the option "yes" activates these GET_** commands also for any other user with access to the ADOxx Modelling Toolkit.  
Calling the command with the option "no" sets the state back (i.e. only administrators can call the commands).

This command is available within both the ADOxx Development Toolkit and the ADOxx Modelling Toolkit.  
However, calling it in the ADOxx Develpoment Toolkit makes no sense as there is no calling restriction anyway!

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "UserMgt" ACTIVATE_READONLY_COMMANDS_FOR_ADOxx ModellingTK yes 
# now the following command can be called
CC "UserMgt" GET_ALL_USERGROUPS
CC "UserMgt" ACTIVATE_READONLY_COMMANDS_FOR_ADOxx ModellingTK no
# now the following command can not be called anymore
CC "UserMgt" GET_ALL_USERGROUPS

{% endraw %}
```
{: .line-numbers}

