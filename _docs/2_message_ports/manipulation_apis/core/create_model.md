---
layout: commandcall
category: CommandCall
title: "CREATE_MODEL"
tags: 1.3 1.5
---

CREATE_MODEL creates a new model.

# Syntax:  

```adoscript
{% raw %}
CC "Core" CREATE_MODEL 	modeltype:strValue 
						modelname:strValue 
						version:strValue
						mgroups:strValue

#--> RESULT ecode:intValue 
			modelid:id 
			threadid:id 
			refids:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modeltype`|strValue, the name of the model type|
|`modelname`|strValue, the name of the model to be created|
|`version`|strValue, the version of the model to be created|
|`mgroups`|strValue, a list of IDs that define the full path of the modelgroup where to create the model|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`modelid`|intValue, the ID of the newly created model.|
|`threadid`|intValue, the ID of the appropriate thread. This can be the ID of an existing modelthread or the ID of a just created thread.|
|`refids`|strValu, contains the IDs of the created modelgroup references (separated by spaces)|

# Remarks:

Modelnames may contain up to 250 characters, the version length may not exceed 20 chars. In opposite to the "New model" dialog and also to RENAME_MODEL, this command allows also empty model names. However, you should never use empty model names here as this may confuse other application components.

In AppLibs with time based versioning the version parameter can be specified in short or long version format.

# See Also:  

[RENAME_MODEL](rename_model.html "RENAME_MODEL")  


