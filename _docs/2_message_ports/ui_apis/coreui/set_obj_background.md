---
layout: commandcall
category: CommandCall
title: "SET_OBJ_BACKGROUND"
tags: 1.3 1.5
---

SET_OBJ_BACKGROUND sets the background color with which a certain object is displayed in a table (browser).

# Syntax:  

```adoscript
{% raw %}
CC "CoreUI" SET_OBJ_BACKGROUND objid:id color:ColorSpec
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`objid`|id|
|`color`|ColorSpec|

# Returns:  

none

# Remarks:

An object's background color is used in the current session until RESET_OBJ_BACKGROUND is called.


# See Also:  

[RESET_OBJ_BACKGROUND](reset_obj_background.html "RESET_OBJ_BACKGROUND")  
[SET_OBJ_FOREGROUND](set_obj_foreground.html "SET_OBJ_FOREGROUND")  


Example 1:

![](/images/RESET_OBJ_BACKGROUND2.png)

```adoscript
{% raw %}

CC "CoreUI" SET_OBJ_BACKGROUND objid:2017 color:$ffee99

{% endraw %}
```
{: .line-numbers}

![](/images/RESET_OBJ_BACKGROUND1.png)


