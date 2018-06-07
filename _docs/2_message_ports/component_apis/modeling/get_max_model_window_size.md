---
layout: commandcall
category: CommandCall
title: "GET_MAX_MODEL_WINDOW_SIZE"
tags: 1.3 1.5
---

GET_MAX_MODEL_WINDOW_SIZE returns the current size of the MDI client area. This is not the maximum size of a model window, but model windows larger than that size cannot be made completely visible. The returned values w and h are the width and the height in pixels.

# Syntax:  

```adoscript
{% raw %}
CC "Modeling" GET_MAX_MODEL_WINDOW_SIZE 


# --> RESULT ecode:intValue w:intValue h:intValue

{% endraw %}
```
{: .line-numbers}

# Parameters:  

none

# Returns:  

|`ecode`|intValue, the return variable ecode is 0 if getting the size was successful, 1 otherwise.|
|`w`|intValue|
|`h`|intValue|

# Remarks:





# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Modeling" SET_WINDOW_POS x:0 y:0
CC "Modeling" GET_MAX_MODEL_WINDOW_SIZE
CC "Modeling" SET_WINDOW_SIZE w:(w) h:(h)

{% endraw %}
```
{: .line-numbers}
Resizes the current model window to fit the whole main window.

