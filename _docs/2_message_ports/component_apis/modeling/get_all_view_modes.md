---
layout: commandcall
category: CommandCall
title: "GET_ALL_VIEW_MODES"
tags: 1.3 1.5
---

GET_ALL_VIEW_MODES returns all view modenames in the model passed with modelid.

# Syntax:  

```adoscript
{% raw %}
CC "Modeling" GET_ALL_VIEW_MODES [ modelid:modelId ] .


# --> RESULT ecode:intValue modenames:strValue

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|modelId|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`modenames`|strValue|

# Remarks:

If no modelid is passed, the current active model will be taken. The modenames are separated with '\n'

The return value ecode is set to 0 if the the command worked, to 1 if an error occured.

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Modeling" GET_ALL_VIEW_MODES
CC "AdoScript" INFOBOX ("Current view modes:\n\n" + modenames)

{% endraw %}
```
{: .line-numbers}
Shows all view modes the current active model.

