---
layout: commandcall
category: CommandCall
title: "CUT_SELECTED"
tags: 1.3 1.5
---

CUT_SELECTED cuts the selected objects in the model passed with modelid into the ADOxx internal clipboard.

# Syntax:  

```adoscript
{% raw %}
CC "Modeling" CUT_SELECTED [ modelid:modelId ] .


# --> RESULT ecode:intValue

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|modelId|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|


# Remarks:

If no modelid is passed, the current active model will be taken.

The return value ecode is set to 0 if the the command worked, to 1 if an error occured.

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Modeling" SELECT_ALL
CC "Modeling" CUT_SELECTED
CC "Modeling" PASTE x:1cm y:15cm

{% endraw %}
```
{: .line-numbers}
Cuts and parstes all objects in the current active model.

