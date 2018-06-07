---
layout: commandcall
category: CommandCall
title: "SET_ZOOM_FACTOR"
tags: 1.3 1.5
---

SET_ZOOM_FACTOR sets the current zoom factor of the model with the passed modelid.

# Syntax:  

```adoscript
{% raw %}
SetZoomFactor :	SET_ZOOM_FACTOR [ modelid:intValue ] zf:intValue.


# --> RESULT ecode:intValue

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|intValue|
|`zf`|intValue|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|


# Remarks:

If no modelid is passed, the current active model will be taken. The percentage value to set is passes with zf

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Modeling" SET_ZOOM_FACTOR zf:50

{% endraw %}
```
{: .line-numbers}
Sets the zoom factor to 50%

