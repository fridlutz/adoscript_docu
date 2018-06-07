---
layout: commandcall
category: CommandCall
title: "SAVE"
tags: 1.3 1.5
---

SAVE saves changes in one model to the database.

# Syntax:  

```adoscript
{% raw %}
ModelSave :	SAVE [ modelid:intValue ].


-->	RESULT ecode:intValue

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|intValue|

# Returns:  

|`ecode`|intValue, the return variable ecode is set to 0 if saving worked, to 1 if an error occured.|


# Remarks:

The id of the model which should be saved is specified with modelid. If no modelid is passed, the current active model will be taken.



# See Also:  



Example 1:

```adoscript
{% raw %}

SEND "GET_ACTIVE_MODEL" to:"Modeling" answer:modelid

CC "Modeling" SAVE modelid:(VAL modelid)
IF (ecode = 1)
{
   CC "AdoScript" INFOBOX "The model could not be saved"
   EXIT
}

{% endraw %}
```
{: .line-numbers}
Saves the changes in the currently active model.

