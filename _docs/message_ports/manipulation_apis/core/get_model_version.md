---
layout: commandcall
category: CommandCall
title: "GET_MODEL_VERSION"
tags: 1.3 1.5
---

GET_MODEL_VERSION returns the version of a model.

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_MODEL_VERSION modelversionid:intValue

#-->RESULT ecode:intValue version:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelversionid`|intValue, the id of the model|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`version`|strValue, the version of the model|


# Remarks:

In modelversionid you must not pass thread ids but only model version ids!

# See Also:  



Example 1:

```adoscript
{% raw %}

# get the id of the current model
SEND "GET_ACTIVE_MODEL" to:"Modeling" answer:modelid
IF (modelid = "")
{
   CC "AdoScript" ERRORBOX "Open a model first!"
   EXIT
}

# get the modeltype of the model
CC "Core" GET_MODEL_VERSION modelversionid:(VAL modelid)

# tell the user the modeltype of the current model
CC "AdoScript" INFOBOX ("The current model is of version: " + version)

{% endraw %}
```
{: .line-numbers}

