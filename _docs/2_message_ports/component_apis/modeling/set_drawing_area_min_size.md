---
layout: commandcall
category: CommandCall
title: "SET_DRAWING_AREA_MIN_SIZE"
tags: 1.3 1.5
---

SET_DRAWING_AREA_MIN_SIZE sets the minimum size of a model's drawing area.

# Syntax:  

```adoscript
{% raw %}
CC "Modeling" SET_DRAWING_AREA_MIN_SIZE	[ modelid:modelId ]
										w:measureValue h:measureValue .


# --> RESULT ecode:intValue .

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|modelId|
|`w`|measureValue|
|`h`|measureValue .|

# Returns:  

|`ecode`|intValue, the return variable ecode is set to 0 if the command call was successful, to 1 otherwise.|


# Remarks:

The model whose minimum drawing area size shall be set can be specified with modelid. Default is the current active model.

The minimum size is specified with w (width) and h (height). For values smaller than 5cm or larger than 50m nothing is done and an error code is returned.

If the new minimum size is larger than the current size, the current size is extended automatically.



# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Modeling" SET_DRAWING_AREA_MIN_SIZE w:30cm h:10cm

{% endraw %}
```
{: .line-numbers}


