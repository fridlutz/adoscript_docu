---
layout: commandcall
category: CommandCall
title: "SET_OBJ_FOREGROUND"
tags: 1.3 1.5
---

SET_OBJ_FOREGROUND sets the foreground color (i.e. the font color) with which a certain object is displayed in a table (browser).

# Syntax:  

```adoscript
{% raw %}
CC "CoreUI" SET_OBJ_FOREGROUND	objid:intValue color:ColorSpec 
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`objid`|intValue|
|`color`|ColorSpec, a color specified either using a predefined color name or a hexadecimal color code.|

# Returns:  

none

# Remarks:

An object's foreground color is used in the current session until RESET_OBJ_FOREGROUND is called.

# See Also:  

[RESET_OBJ_FOREGROUND](reset_obj_foreground.html "RESET_OBJ_FOREGROUND")  
[SET_OBJ_BACKGROUND](set_obj_background.html "SET_OBJ_BACKGROUND")  


Example 1:

```adoscript
{% raw %}

CC "CoreUI" SET_OBJ_FOREGROUND objid:2017 color:red

{% endraw %}
```
{: .line-numbers}

