---
layout: commandcall
category: CommandCall
title: "RESET_OBJ_BACKGROUND"
tags: 1.3 1.5
---

RESET_OBJ_BACKGROUND resets the background color with which a certain object is displayed in a table (browser) to the default color.

# Syntax:  

```adoscript
{% raw %}
CC "CoreUI" RESET_OBJ_BACKGROUND objid:intValue .

{% endraw %}
```
{: .line-numbers}


# Parameters:  

|`objid`|intValue|

# Returns:  

none

# Remarks:

An object's background color can be set with SET_OBJ_BACKGROUND.

# See Also:  

[SET_OBJ_BACKGROUND](set_obj_background.html "SET_OBJ_BACKGROUND")  
[RESET_OBJ_FOREGROUND](reset_obj_foreground.html "RESET_OBJ_FOREGROUND")  


Example 1:

![](/images/RESET_OBJ_BACKGROUND1.png)

```adoscript
{% raw %}

CC "CoreUI" RESET_OBJ_BACKGROUND objid:2017

{% endraw %}
```
{: .line-numbers}

![](/images/RESET_OBJ_BACKGROUND2.png)

