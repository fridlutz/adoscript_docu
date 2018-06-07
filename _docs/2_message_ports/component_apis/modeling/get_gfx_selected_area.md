---
layout: commandcall
category: CommandCall
title: "GET_GFX_SELECTED_AREA"
tags: 1.3 1.5
---

GET_GFX_SELECTED_AREA returns the points x1, y1, x2 and y2 of the selected gfx area as measure values of the passed modelid.

# Syntax:  

```adoscript
{% raw %}
CC "Modeling" GET_GFX_SELECTED_AREA [ modelid:modelId ] .


# -->	RESULT ecode:intValue x1:measureValue y1:measureValue
	           x2:measureValue y2:measureValue

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|modelId|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`x1`|measureValue|
|`y1`|measureValue|
|`x2`|measureValue|
|`y2`|measureValue|

# Remarks:

If no modelid is passed, the current active model will be taken.

The return variable ecode is set to 0 if the command worked, to 1 if an error occured.

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Modeling" debug GET_GFX_SELECTED_AREA

{% endraw %}
```
{: .line-numbers}


