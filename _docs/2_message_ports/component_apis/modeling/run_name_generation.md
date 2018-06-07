---
layout: commandcall
category: CommandCall
title: "RUN_NAME_GENERATION"
tags: 1.3 1.5
---

RUN_NAME_GENERATION runs the name generation for all objects in the model with the passed modelid.

# Syntax:  

```adoscript
{% raw %}
CC "Modeling" RUN_NAME_GENERATION modelid:intValue .


# --> RESULT ecode:intValue changes:intValue

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|intValue|

# Returns:  

|`ecode`|intValue, the resulting ecode is either 0 (no error) or 1 (error).|
|`changes`|intValue, the result value changes states how many objects have been renamed.|

# Remarks:





# See Also:  



Example 1:

```adoscript
{% raw %}

# Get the model id of the currently active model:
SEND "GET_ACTIVE_MODEL" to:"Modeling" answer:modelid
SET n_mid:(VAL modelid)

# Name the objects in the model:
CC "Modeling" RUN_NAME_GENERATION modelid:(n_mid)
IF (ecode != 0)
{
  CC "AdoScript" ERRORBOX "[mynamegen-01]\nDie Objektnamen konnten nicht erzeugt werden." title:"Error"
  EXIT
}

# Inform user how many objects have been renamed:
CC "AdoScript" INFOBOX "Es wurden " + STR changes + " Objekte neu benannt."

{% endraw %}
```
{: .line-numbers}
This AdoScript runs the name generation function in the currently active model. Afterwards the user is informed how many objects have been renamed.

