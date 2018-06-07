---
layout: commandcall
category: CommandCall
title: "IS_MODEL_LOADED"
tags: 1.3 1.5
---

IS_MODEL_LOADED returns true if the specified model is loaded in the Core! This does not necessarily mean, that a model window exists!

# Syntax:  

```adoscript
{% raw %}
CC "Core" IS_MODEL_LOADED modelid:intValue

#-->RESULT ecode:intValue isloaded:[0|1]
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|intValue, the ID of the model|

# Returns:  

|`ecode`|intValue, is 0 in case of success or an error code if the model does not exist.|
|`isloaded`|intValue, is 1 if the model is loaded or 0 if the model is not loaded|

# Remarks:



# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Core" GET_MODEL_ID modelname:"A" modeltype:"Gesch�ftsproze�modell"

IF (ecode = 0)
{
   CC "Core" IS_MODEL_LOADED modelid:(modelid)
   IF (isloaded = 0)
   {
     CC "AdoScript" INFOBOX ""The model is not loaded. Do you want to open it???"
     # the rest is up to you :)
   }
   ELSE
   {
     # the model is loaded -> do whatever you want to do...
   }
}
ELSE
{
   CC "AdoScript" ERRORBOX "The model does not exist!"
}

{% endraw %}
```
{: .line-numbers}
Before you execute this example, create a model of type "Gesch�ftsproze�modell" called "A". Then execute the example: first the model id of the model is retrieved and it is queried whether it is loaded or not!

