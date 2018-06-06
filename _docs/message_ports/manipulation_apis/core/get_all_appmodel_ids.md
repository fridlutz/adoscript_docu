---
layout: commandcall
category: CommandCall
title: "GET_ALL_APPMODEL_IDS"
tags: 1.3 1.5
---

The command GET_ALL_APPMODEL_IDS returns a list of all appmodels.

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_ALL_APPMODEL_IDS

#--> RESULT appmodelids:idlist
{% endraw %}
```
{: .line-numbers}

# Parameters:  

none

# Returns:  

|`appmodelids`|strVal, a list with all model versions|

# Remarks:

You can get more informations about the appmodel with the command GET_APPMODEL_INFO

# See Also:  

[GET_APPMODEL_INFO](get_appmodel_info.html "GET_APPMODEL_INFO")  


Example 1:

```adoscript
{% raw %}

SET sAppModels:("All Application Models:\n\n")
CC "Core" GET_ALL_APPMODEL_IDS
FOR appModelId in:(appmodelids)
{
  CC "Core" GET_APPMODEL_INFO appmodelid:(VAL appModelId)
  IF (onversions)
  {
    SET sAppModels:(sAppModels + appmodelname + "\n")
  }
}
CC "AdoScript" INFOBOX (sAppModels)

{% endraw %}
```
{: .line-numbers}

Displays all version specific application models in a infobox.  
(Replace "onversions" with "onthreads" to get all thread specific application models)

