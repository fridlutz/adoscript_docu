---
layout: commandcall
category: CommandCall
title: "GET_VIEW_MODE"
tags: 1.3 1.5
---

GET_VIEW_MODE returns the current modename in the model passed with modelid.

# Syntax:  

```adoscript
{% raw %}
CC "Modeling" GET_VIEW_MODE [ modelid:modelId ] .


# --> RESULT ecode:intValue modeltype:strValue modename:strValue

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|modelId|

# Returns:  

|`ecode`|intValue, the return value ecode is set to 0 if the the command worked, to 1 if an error occured.|
|`modeltype`|strValue|
|`modename`|strValue|

# Remarks:

If no modelid is passed, the current active model will be taken.


# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Modeling" debug GET_VIEW_MODE

{% endraw %}
```
{: .line-numbers}
Shows the current view mode in the current active model

