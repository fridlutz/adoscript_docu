---
layout: commandcall
category: CommandCall
title: "GET_ACTIVE_VARIANT"
tags: 1.3 1.5
---

GET_ACTIVE_VARIANT gets the active variant of a model.

# Syntax:  

```adoscript
{% raw %}
CC "Drawing" GET_ACTIVE_VARIANT	modelid:intValue

-->RESULT variant:strValue ecode:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|intValue, holds the ID of a model.|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`variant`|strValue, holds the name of the active variant of that model.|

# Remarks:

As for all commands of the "Drawing" message port, it is not required here to have a model window opened.

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Modeling" GET_ACT_MODEL
CC "Drawing" GET_ACTIVE_VARIANT modelid:(modelid)
CC "AdoScript" INFOBOX ("Active variant: " + variant)

{% endraw %}
```
{: .line-numbers}

