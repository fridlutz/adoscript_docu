---
layout: commandcall
category: CommandCall
title: "SET_AUTOSAVE"
tags: 1.3 1.5
---

SET_AUTOSAVE changes the autosave settings.

# Syntax:  

```adoscript
{% raw %}
CC "Modeling" SET_AUTOSAVE	Enabling [ changes:intValue] .


Enabling :	on | off | enabled:intValue .


# --> RESULT ecode:intValue .

{% endraw %}
```
{: .line-numbers}

# Parameters:  

on
off
|`enabled`|intValue|
|`changes`|intValue|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|


# Remarks:

The user can change the autosave settings in the dialog "Auto save..." in the menu "Extra":

![](/images/SET_AUTOSAVE.png)

Autosave is turned on by passing the argument on or enabled:1. It can be turned off by passing off or enabled:0.  
The argument changes specifies after how many model changes (e.g. create a new class, change an attribute, ...) the model should be automatically saved. The default value is 1 (i.e. autosave after each single change).


# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Modeling" GET_AUTOSAVE
CC "Modeling" SET_AUTOSAVE off
# ... (some actions)
CC "Modeling" SET_AUTOSAVE enabled:(enabled) changes:(changes)

{% endraw %}
```
{: .line-numbers}
The first CC saves the current autosave status. After that, autosaving is switched off.  
The last CC restores the original autosave settings.

