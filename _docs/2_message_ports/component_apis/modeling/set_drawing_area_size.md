---
layout: commandcall
category: CommandCall
title: "SET_DRAWING_AREA_SIZE"
tags: 1.3 1.5
---

SET_DRAWING_AREA_SIZE sets the drawing area size to w and h as measure values to the passed modelid.

# Syntax:  

```adoscript
{% raw %}
CC "Modeling" SET_DRAWING_AREA_SIZE [ modelid:modelId ] w:measureValue h:measureValue .


# --> RESULT ecode:intValue

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|modelId|
|`w`|measureValue|
|`h`|measureValue|

# Returns:  

|`ecode`|intValue, the return variable ecode is set to 0 if the command worked, to 1 if an error occured.|


# Remarks:

If no modelid is passed, the current active model will be taken.



# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Modeling" SET_DRAWING_AREA_SIZE w:20cm h:20cm

{% endraw %}
```
{: .line-numbers}
Sets the drawing area size to 20 x 20.

