---
layout: commandcall
category: CommandCall
title: "SAVE_MODEL_AS"
tags: 1.3 1.5
---

SAVE_MODEL_AS saves a model either as a new version or as an entirely new model.

# Syntax:  

SaveModelAsNewVersion  
```adoscript
{% raw %}
CC "Core SAVE_MODEL_AS 	modelid:intValue
						basename:strValue 
						version:strValue
						[ mgroupids:strValue ] 
						[ moverefs ]

#--> RESULT ecode:intValue
			newthreadid:intValue 
			newmodelid:intValue 
			refids:strValue
{% endraw %}
```
{: .line-numbers}

SaveModelAsNewMode  
```adoscript
{% raw %}
CC "Core" SAVE_MODEL_AS modelid:intValue version:strValue

#-->RESULT ecode:intValue newmodelid:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|intValue, the id of the model|
|`basename`|strValue, specifies the new name when saving a model as a new model|
|`version`|strValue, specifies the new version|
|`mgroupids`|strValue, the modelgroups where the new model will be created|
|`moverefs`|modifier, if given, incoming model references will be moved to the new model thread (but only if the user has write access on the source model!).|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`newthreadid`|intValue,  the ID of the new thread|
|`newmodelid`|intValue, the ID of the new model|
|`refids`|strValue, a list with the IDs of all references|

# Remarks:

If this parameter mgroupids is not specified or empty, ADOxx will use the modelgroups of the source model; you cannot create models in the modelpool.

As SAVE_MODEL_AS is a core command, the modeling window is not updated correctly (see ). Thus the method must only be applied to models that are not currently opened in the modeling window.

# See Also:  



Example 1:

```adoscript
{% raw %}

SEND "GET_ACTIVE_MODEL" to:"Modeling" answer:modelid
CC "Modeling" CLOSE modelid:(VAL modelid)
CC "Core" LOAD_MODEL modelid:(VAL modelid)
CC "Core" SAVE_MODEL_AS modelid:(VAL modelid)
        basename:"My new model 2" version:"1.0"
IF (ecode = 0) {
   CC "AdoScript" INFOBOX "The model has sucessfully been saved!"
}
CC "Modeling" CREATE_WINDOW_FOR_LOADED_MODEL modelid:(newmodelid)

{% endraw %}
```
{: .line-numbers}

Retrieves the currently opened model and saves it as a new model called "My new model". As the model used with SAVE_MODEL_AS must not be opened in the model editor we have to close the model window first and then load the model only to the core. After the model has been saved, a modeling window is opened for the new model (the original model is automatically discareded by SAVE_MODEL_AS).  
