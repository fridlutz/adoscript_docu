---
layout: commandcall
category: CommandCall
title: "GET_MODEL_CHANGECOUNTER"
tags: 1.3 1.5
---

GET_MODEL_CHANGECOUNTER retrieves the overall change counter of a model. The change counter is updated everytime an attribute changes, a instance is created or deleted, etc.

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_MODEL_CHANGECOUNTER modelid:intValue

#-->RESULT ecode:intValue changecounter:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|intValue, the id of the model|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`changecounter`|intValue, if a model with the specified ID exists, the return variable changecounter is set to the current changecounter of the model.|


# Remarks:

This command returns a session-specific change counter. This means that after restarting the ADOxx Modelling Toolkit, it is always reset to "0".

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Core" GET_MODEL_ID modelname:"A" modeltype:"Gesch�ftsproze�modell"

IF (ecode = 0)
{
   CC "Core" GET_MODEL_CHANGECOUNTER modelid:(modelid)
   CC "AdoScript" INFOBOX ("The current changecounter is: " + STR (changecounter))
}
ELSE
{
   CC "AdoScript" ERRORBOX "The model does not exist!"
}

{% endraw %}
```
{: .line-numbers}

Before you execute this example, create a model of type "Gesch�ftsproze�modell" called "A". Then execute the example: first the model id of the model is retrieved and then the changecounter is queried.

