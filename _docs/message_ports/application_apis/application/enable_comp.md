---
layout: commandcall
category: CommandCall
title: "ENABLE_COMP"
tags: 1.3 1.5
---

The command ENABLE_COMP enables one of the selected components.

# Syntax:  

```adoscript
{% raw %}
CC "Application" ENABLE_COMP 	[ all ] [ acquisition ] [ modeling ] [ analysis ]�
								[ simulation ] [ evaluation ] [ importexport ]

#--> RESULT ecode:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

none

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|

# Remarks:

By passing all, all components are enabled, if they had been disabled using all before. (If components have been disabled individually, they also have to be enabled individually, and parameter all will not work!)

A disabled component can not be selected by the user. Disabled components are visualized as grayed icons (see DISABLE_COMP.png) .

Enabled components are displayed in color and can be selected by the user  (see ENABLE_COMP.png) .

# See Also:  

[DISABLE_COMP](disable_comp.html "DISABLE_COMP")  


Example 1:  
First disables the modeling component and shows an infobox so that the user can see the result. The disables all, after that enables only the modeling and finally all components.

```adoscript
{% raw %}

CC "Application" DISABLE_COMP modeling
CC "AdoScript" INFOBOX "Modeling has been disabled"
CC "Application" DISABLE_COMP all
CC "AdoScript" INFOBOX "All components have been disabled"
CC "Application" ENABLE_COMP modeling
CC "AdoScript" INFOBOX "Modeling has been enabled again"
CC "Application" ENABLE_COMP all
CC "AdoScript" INFOBOX "All components have been enabled"

{% endraw %}
```
{: .line-numbers}

