---
layout: commandcall
category: CommandCall
title: "GET_DRAWING_AREA_SIZE"
tags: 1.3 1.5
---

GET_DRAWING_AREA_SIZE returns the size of the drawing area of the given model passed witn modelid.

# Syntax:  

```adoscript
{% raw %}
CC "Modeling" GET_DRAWING_AREA_SIZE [ modelid:intValue ].


# --> RESULT ecode:intValue w:measureValue h:measureValue

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|intValue|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`w`|measureValue|
|`h`|measureValue|

# Remarks:

The model has to be open in a modeling window for this command. The command will not work, if the model is only loaded in the core! If no modelid is passed, the current active model will be taken.

The return arguments (w,h) contain the width and the height of the drawing area. The return value ecode is set to 0 if the visible are could be computed.

# See Also:  



Example 1:

```adoscript
{% raw %}

SEND "GET_ACTIVE_MODEL" to:"Modeling" answer:modelid

CC "Modeling" debug GET_DRAWING_AREA_SIZE modelid:(VAL modelid)

{% endraw %}
```
{: .line-numbers}


