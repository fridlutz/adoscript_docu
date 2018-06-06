---
layout: commandcall
category: CommandCall
title: "GET_WINDOW_POS_SIZE"
tags: 1.3 1.5
---

GET_WINDOW_POS_SIZE returns the position x, y and the size w, h of the model window with the passed modelid in pixel.

# Syntax:  

```adoscript
{% raw %}
CC "Modeling" GET_WINDOW_POS_SIZE [ modelid:intValue ] .


# --> RESULT ecode:intValue x:intValue y:intValue w:intValue h:intValue

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|intValue|

# Returns:  

|`ecode`|intValue, the return variable ecode is set to 0 if setting worked, to 1 if an error occured or the model window is minimized or maximized.|
|`x`|intValue|
|`y`|intValue|
|`w`|intValue|
|`h`|intValue|

# Remarks:

If no modelid is passed, the current active model will be taken.



# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Modeling" GET_WINDOW_STATE
IF (state != "normal")
{
  CC "AdoScript" INFOBOX ("The current model window is maximized or minimized!")
  EXIT
}
CC "Modeling" debug GET_WINDOW_POS_SIZE

{% endraw %}
```
{: .line-numbers}
Shows the size and position of the current model window.

