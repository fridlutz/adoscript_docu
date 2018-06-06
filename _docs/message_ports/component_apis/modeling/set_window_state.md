---
layout: commandcall
category: CommandCall
title: "SET_WINDOW_STATE"
tags: 1.3 1.5
---

SET_WINDOW_STATE sets the state of the model window with the passed modelid.

# Syntax:  

```adoscript
{% raw %}
SetWindowState :	SET_WINDOW_STATE [ modelid:intValue ] state:stateVal .


statVal	"max" | "min" | "normal"


# --> RESULT ecode:intValue

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|intValue|
|`state`|stateVal, the state value must be "max", "min" or "normal".|

# Returns:  

|`ecode`|intValue, the return variable ecode is set to 0 if setting worked, to 1 if an error occured.|


# Remarks:

If no modelid is passed, the current active model will be taken.

Only 1 window can be maximized. The status of the previous maximized window will be set to normal.



# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Modeling" SET_WINDOW_STATE state:"min"

{% endraw %}
```
{: .line-numbers}
Minimizes the current model window.

