---
layout: commandcall
category: CommandCall
title: "GET_SCREEN_RES"
tags: 1.3 1.5
---

The command GET_SCREEN_RES returns the screen resolution w and h in pixels.

# Syntax:  

```adoscript
{% raw %}
CC "Application" GET_SCREEN_RES

#--> RESULT ecode:intValue w:intValue h:intValue 
{% endraw %}
```
{: .line-numbers}

# Parameters:  

none

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`w`|intValue, the horizontal screen resolution in pixels.|
|`h`|intValue, the vertical screen resolution in pixels.|

# Remarks:



# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Application" debug GET_SCREEN_RES

{% endraw %}
```
{: .line-numbers}

