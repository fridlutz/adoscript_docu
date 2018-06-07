---
layout: commandcall
category: CommandCall
title: "EXEC_NEW_DLG"
tags: 1.3 1.5
---

EXEC_NEW_DLG starts the dialog for creating new models and returns the model id of the newly created model.

# Syntax:  

```adoscript
{% raw %}
CC "Modeling" EXEC_NEW_DLG [ modelname:strValue ] 
						   [ version:strValue ] 
						   [ modeltype:strValue ] 
						   [ target-mgroupid:intValue ] 
						   [ show-models [ show-all-versions ] ] .


# --> intValue

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelname`|strValue|
|`version`|strValue|
|`modeltype`|strValue|
|`target-mgroupid`|intValue|
|`show-models`|modifier|
|`show-all-versions `|modifier|

# Returns:  

intValue

# Remarks:

When the user aborts the dialog, an empty string is returned.

You can specify the modelname, version, modeltype and the target-mgroupid.  
(Writing target-modelgroupid has the same meaning as target-mgroupid, but is deprecated.)  
With show-models you can show all the models in the new dialog and you can expand their versions with show-all-versions.


# See Also:  



Example 1:

```adoscript
{% raw %}

SEND "EXEC_NEW_DLG modelname:\"My Model\" modeltype:\"Sample Model\" show-models" to:"Modeling" answer:modelid
IF (modelid != "")
{
   CC "AdoScript" INFOBOX ("You created the model with id " + modelid)

{% endraw %}
```
{: .line-numbers}


