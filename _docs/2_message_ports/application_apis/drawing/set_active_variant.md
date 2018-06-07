---
layout: commandcall
category: CommandCall
title: "SET_ACTIVE_VARIANT (Drawing)"
tags: 1.3 1.5
---

SET_ACTIVE_VARIANT sets the active variant of a model.

# Syntax:  

```adoscript
{% raw %}
CC "Drawing" SET_ACTIVE_VARIANT	modelid:intValue variant:strValue

# --> RESULT ecode:intValue .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|intValue, the ID of the model|
|`variant`|strValu, the name of the variant to activate in the model.|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|


# Remarks:

As for all commands of the "Drawing" message port, it is not required here to have a model window opened. So the variant can be activated easily before generationg graphics using CC "Drawing" GEN_GFX_FILE / GEN_GFX_STR.

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Drawing" SET_ACTIVE_VARIANT
       modelid:(modelid) variant:"With swimlanes"

{% endraw %}
```
{: .line-numbers}

