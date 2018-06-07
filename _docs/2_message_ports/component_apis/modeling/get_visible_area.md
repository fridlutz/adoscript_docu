---
layout: commandcall
category: CommandCall
title: "GET_VISIBLE_AREA"
tags: 1.3 1.5
---

GET_VISIBLE_AREA returns the bounds of the currently visible area of the given model passed with modelid.

# Syntax:  

```adoscript
{% raw %}
CC "Modeling" GET_VISIBLE_AREA [ modelid:intValue ].


# --> RESULT ecode:intValue x1:measureValue y1:measureValue x2:measureValue y2:measureValue

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|intValue|

# Returns:  

|`ecode`|intValue, the return value ecode is set to 0 if the visible are could be computed.|
|`x1`|measureValue|
|`y1`|measureValue|
|`x2`|measureValue|
|`y2`|measureValue|

# Remarks:

If no modelid is passed, the current active model will be taken.

The return arguments (x1,y1) and (x2,y2) contain the upper left and lower right coordinates of the visible rectangle in the modeling window.

# See Also:  



Example 1:

```adoscript
{% raw %}

SEND "GET_ACTIVE_MODEL" to:"Modeling" answer:modelid

CC "Modeling" debug GET_VISIBLE_AREA modelid:(VAL modelid)

{% endraw %}
```
{: .line-numbers}


