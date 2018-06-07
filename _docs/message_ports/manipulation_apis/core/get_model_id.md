---
layout: commandcall
category: CommandCall
title: "GET_MODEL_ID"
tags: 1.3 1.5
---

GET_MODEL_ID retrieves the id of a model.

# Syntax:  

GetModelIDByModelName  
```adoscript
{% raw %}
CC "Core" GET_MODEL_ID modelname:strValue [ version:strValue ] modeltype:strValue
{% endraw %}
```
{: .line-numbers}

GetModelIDByObject  
```adoscript
{% raw %}
CC "Core" GET_MODEL_ID objid:intValue
{% endraw %}
```
{: .line-numbers}

```adoscript
{% raw %}
#-->RESULT ecode:intValue modelid:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelname`|strValue, the name of the model|
|`version`|strValue, the version of the model|
|`modeltype`|strValue, the name of the model type of the model|
|`objid`|strValue, the ID of an object|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`modelid`|intValue, if a model with the specified name or object exists, the return variable modelid is set to the id of the model. Otherwise, modelid is set to -1 .|

# Remarks:

The modelid can either be retrieved by specifying the modelname or by specifying an object that is contained in the model.#

When retrieving the modelid by name, the modelname has to be specified with the argument modelname, the modeltype is specified with the argument modeltype. If the model is versioned, the version can be specified with the argument version (either in the long format e.g. "Januar 2000" or in the short format e.g. "20000100").


# See Also:  



Example 1:

Get the model id by specifying the name  
```adoscript
{% raw %}

CC "Core" GET_MODEL_ID modelname:"A" modeltype:"Sample Model"

IF (ecode = 0)
{
   CC "Core" debug GET_MODEL_INFO modelid:(modelid)
}
ELSE
{
   CC "AdoScript" ERRORBOX "The model does not exist!"
}

{% endraw %}
```
{: .line-numbers}
Before you execute this example, create a model of type "Sample Model" called "A". Then execute the example: first the model id of the model is retrieved and then for this model general information about the model is queried.

Example 2:

When retrieving the modelid by an object contained in the model, the id of the object has to be passed in the argument objid.  
If the returned eCode is CLASSINSTANCE_NOT_EXISTING you passed an unknown objid.  
Get the model id by specifying an object  
```adoscript
{% raw %}

# get all selected objects
CC "Modeling" GET_SELECTED
IF (objids = "")
{
   CC "AdoScript" ERRORBOX "No object has been selected!"
   EXIT
}

# from the list of selected objects, extract the first objectid
SET firstselected:(token(objids,0," "))

# get the modelid containg the selected object
CC "Core" GET_MODEL_ID objid:(VAL firstselected)

# if the core returned the modelid, use it to retrieve some modelinformation
IF (ecode = 0)
{
   CC "Core" debug GET_MODEL_INFO modelid:(modelid)
}
ELSE
{
   CC "AdoScript" ERRORBOX "The model does not exist!"
}

{% endraw %}
```
{: .line-numbers}
Before you execute this example, open a model and select an object within the model. Then execute the script: the script retrieves the id of the selected object. Theh with GET_MODEL_ID it gets the id of the model containing the selected object. Finally it prints general model information for the model.  
