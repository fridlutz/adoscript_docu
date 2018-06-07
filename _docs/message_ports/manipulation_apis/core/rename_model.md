---
layout: commandcall
category: CommandCall
title: "RENAME_MODEL"
tags: 1.3 1.5
---

RENAME_MODEL renames a model.

# Syntax:  

```adoscript
{% raw %}
CC "Core" RENAME_MODEL modelid:id basename:strValue version:strValue

#-->RESULT ecode:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|intValue, the id of the model that should be renamed|
|`basename`|strValue, the new name of the model|
|`version`|strValue, the new version of the model|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|

# Remarks:

The version can be specified in long or in short format.

Error code "52" means that the new model name is not unique. It is quite typical and should be caught.

# See Also:  



Example 1:

```adoscript
{% raw %}

SEND "GET_ACTIVE_MODEL" to:"Modeling" answer:modelid
CC "Core" RENAME_MODEL modelid:(VAL modelid) basename:"My new modelname" version:"2.0"
IF (ecode = 0)
{
   CC "AdoScript" INFOBOX "The model has sucessfully been renamed!"
}

{% endraw %}
```
{: .line-numbers}
Retrieves the currently opened model and renames it to "My new modelname 2.0".  
