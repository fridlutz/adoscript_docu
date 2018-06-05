---
layout: commandcall
category: CommandCall
title: "SET_WINDOW_POS"
tags: 1.3 1.5
---

SET_WINDOW_POS sets the position of the model window with the passed modelid.

# Syntax:  

```adoscript
{% raw %}
CC "Modeling" SET_Window_POS [ modelid:intValue ] x:intValue w:intValue .


# --> RESULT ecode:intValue

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|intValue|
|`x`|intValue|
|`w`|intValue|

# Returns:  

|`ecode`|intValue, the return variable ecode is set to 0 if setting worked, to 1 if an error occured.|


# Remarks:

If no modelid is passed, the current active model will be taken. The passed x and y values are pixel.



# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Modeling" SET_WINDOW_POS x:0 y:0

{% endraw %}
```
{: .line-numbers}
Sets the position of the current active model window to the top left corner.

