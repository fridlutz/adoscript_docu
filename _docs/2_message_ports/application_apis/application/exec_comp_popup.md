---
layout: commandcall
category: CommandCall
title: "EXEC_COMP_POPUP"
tags: 1.3 1.5
---

The command EXEC_COMP_POPUP executes the popupmenu for choosing a component. (see EXEC_COMP_POPUP.png)

# Syntax:  

```adoscript
{% raw %}
CC "Application" EXEC_COMP_POPUP

#--> RESULT ecode:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

none

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|

# Remarks:



# See Also:



Example 1:

```adoscript
{% raw %}

CC "Application" EXEC_COMP_POPUP

{% endraw %}
```
{: .line-numbers}
