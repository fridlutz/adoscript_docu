---
layout: commandcall
category: CommandCall
title: "DELETE_MODEL"
tags: 1.3 1.5
---

DELETE_MODEL deletes an existing model.

# Syntax:  

```adoscript
{% raw %}
CC "Core" DELETE_MODEL modelid:intValue

#-->RESULT ecode:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|intValue, the id of the model that should be deleted|

# Returns:  

|`ecode`|intValue, contains the error code or is 0 in case of success.|

# Remarks:

The model that should be deleted MUST NOT be opened in the shell!

Ensure that you call CC "Modeling" CLOSE before deleting, else ADOxx will crash!

# See Also:  



Example 1:

```adoscript
{% raw %}

# let the user select a model
CC "CoreUI" MODEL_SELECT_BOX 

# check if the model is currently opened
CC "Modeling" IS_OPENED modelid:(VAL token(modelids,0," "))

IF (isopened = 1)
{
   CC "Modeling" CLOSE modelid:(VAL token(modelids,0," "))
}

# delete the model
CC "Core" DELETE_MODEL modelid:(VAL token(modelids,0," "))

IF (ecode != 0)
{
   CC "AdoScript" INFOBOX "Error! Delete failed"
}

{% endraw %}
```
{: .line-numbers}

