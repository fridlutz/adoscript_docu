---
layout: commandcall
category: CommandCall
title: "SET_GFX_SELECTED_AREA"
tags: 1.3 1.5
---

SET_GFX_SELECTED_AREA sets a gfx selection area with the points x1, y1, x2 and y2 as measure values to the passed modelid.

# Syntax:  

```adoscript
{% raw %}
CC "Modeling" SET_GFX_SELECTED_AREA [ modelid:modelId ] x1:measureValue y1:measureValue
	                                                                      x2:measureValue y2:measureValue.


# --> RESULT ecode:intValue

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|modelId|
|`x1`|measureValue|
|`y1`|measureValue|
|`x2`|measureValue|
|`y2`|measureValue.|

# Returns:  

|`ecode`|intValue, the return variable ecode is set to 0 if the command worked, to 1 if an error occured.|


# Remarks:

If no modelid is passed, the current active model will be taken.




# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Modeling" SET_GFX_SELECTED_AREA x1:1cm y1:1cm x2:5cm y2:5cm
CC "AdoScript" INFOBOX ("A gfx area should be selected now!")
CC "Modeling" REMOVE_GFX_SELECTED_AREA
CC "AdoScript" INFOBOX ("The gfx area should be removed now!")

{% endraw %}
```
{: .line-numbers}
Sets and removes a gfx selection.

