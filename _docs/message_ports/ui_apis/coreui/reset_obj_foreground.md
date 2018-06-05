---
layout: commandcall
category: CommandCall
title: "RESET_OBJ_FOREGROUND"
tags: 1.3 1.5
---

RESET_OBJ_FOREGROUND resets the foreground color (i.e. the font color) with which a certain object is displayed in a table (browser) to the default color.

# Syntax:  

```adoscript
{% raw %}
CC "CoreUI" RESET_OBJ_FOREGROUND objid:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`objid`|intValue|

# Returns:  

none

# Remarks:



# See Also:  

[SET_OBJ_FOREGROUND](set_obj_foreground.html "SET_OBJ_FOREGROUND")  
[RESET_OBJ_BACKGROUND](reset_obj_background.html "RESET_OBJ_BACKGROUND")  


Example 1:

![](/images/RESET_OBJ_FOREGROUND1.png)

```adoscript
{% raw %}

CC "CoreUI" RESET_OBJ_FOREGROUND objid:2017

{% endraw %}
```
{: .line-numbers}

![](/images/RESET_OBJ_FOREGROUND2.png)
