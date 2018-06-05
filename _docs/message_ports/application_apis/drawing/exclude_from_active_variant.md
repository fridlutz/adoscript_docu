---
layout: commandcall
category: CommandCall
title: "EXCLUDE_FROM_ACTIVE_VARIANT"
tags: 1.3 1.5
---

EXCLUDE_FROM_ACTIVE_VARIANT excludes a modeling object or a connector from the active variant of a model.

# Syntax:  

```adoscript
{% raw %}
CC "Drawing" EXCLUDE_FROM_ACTIVE_VARIANT modelid:intValue objid:intValue

# --> RESULT ecode:intValue .

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|intValue, the ID of the model|
|`objid`|intValue, the ID of the modeling object|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|


# Remarks:

The parameters of this CC are the ID of a model and the ID of a modeling object or connector which shall be excluded from the active variant of that model.

As for all commands of the "Drawing" message port, it is not required here to have a model window opened.

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Modeling" GET_ACT_MODEL
CC "Modeling" GET_SELECTED
FOR objid in:(objids) {
    CC "Drawing" EXCLUDE_FROM_ACTIVE_VARIANT
            modelid:(modelid) objid:(VAL objid)
}

{% endraw %}
```
{: .line-numbers}

