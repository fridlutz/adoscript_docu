---
layout: commandcall
category: CommandCall
title: "SET_STATUS"
tags: 1.3 1.5
---

SET_STATUS sets the text of the application window's status bar.

# Syntax:  

```adoscript
{% raw %}
CC "Application" SET_STATUS strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`<main_parameter>`|strValue, contains the status to be set|

# Returns:  

none

# Remarks:



# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Application" SET_STATUS "Please wait..."
# ... (do something)
CC "Application" SET_STATUS ""  # clear status bar text

{% endraw %}
```
{: .line-numbers}


