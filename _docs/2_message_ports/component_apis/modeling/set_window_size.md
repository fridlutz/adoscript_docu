---
layout: commandcall
category: CommandCall
title: "SET_WINDOW_SIZE"
tags: 1.3 1.5
---

SET_WINDOW_SIZE sets the size of the model window with the passed modelid.

# Syntax:  

```adoscript
{% raw %}
CC "Modeling" SET_WINDOW_SIZE [ modelid:intValue ] w:intValue h:intValue .


-->	RESULT ecode:intValue

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|intValue|
|`w`|intValue|
|`h`|intValue|

# Returns:  

|`ecode`|intValue, the return variable ecode is set to 0 if setting worked, to 1 if an error occured.|


# Remarks:

If no modelid is passed, the current active model will be taken. The passed width value w and the height value h are pixel.



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
Resizes the current model window to fit the whole ADOxx window.

