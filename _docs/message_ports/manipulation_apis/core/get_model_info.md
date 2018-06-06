---
layout: commandcall
category: CommandCall
title: "GET_MODEL_INFO"
tags: 1.3 1.5
---

Is a command call of the message port "Core" and returns name, type, library and access information about a model.

# Syntax:

```adoscript
{% raw %}
CC "Core"	GET_MODEL_INFO	modelid: intValue

#--> RESULT modelname:strValue ver:strValue version:strValue version:strValue
			threadid:id modeltype:strValue libid:id libtype:strValue
			libname:strValue access:strValue ecode:intValue 
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|intValue, specifies the ID of the model|

# Returns:  

|`modelname`|strValue|
|`ver`|strValue|
|`version`|strValue|
|`threadid`|id|
|`modeltype`|strValue|
|`libid`|id|
|`libtype`|"bp" | "we"|
|`libname`|strValue|
|`access`|"none" | "write" | "read"|
|`ecode`|intValue|

# Remarks:

The model has to be specified by passing the model ID with modelid.

The name of the model is returned with modelname, the model type with modeltype and the ID of the related library is returned with libid.

If the library is versioned (time-related), the modelversion is returned in long format with version and in short format with ver.  
For time-related versioned libraries the thread ID (see "Introduction on Versioning") is returned with threadid.

The return value access holds the value "none" if the model is not loaded. If it is loaded, then "read" or "write" is returned, depending on whether the current user may read or write to that model. (Actually in that case the same info is returned as with command GET_ACCESS_MODE.)

# See Also:  

[GET_ACT_MODEL](get_act_model.html "GET_ACT_MODEL")  


Example 1:

```adoscript
{% raw %}
CC "Modeling" GET_ACT_MODEL
IF (ecode = 0) {
    CC "Core" GET_MODEL_INFO modelid:(VAL modelid)
    CC "AdoScript" INFOBOX (
        "The active model is \"" + modelname + "\" (" + modeltype + ")"
    )
} ELSE {
    CC "AdoScript" ERRORBOX "No model is opened!"
}
{% endraw %}
```
{: .line-numbers}

Before you execute this example, open an existing model. The script retrieves the id of the currently opend model and calls GET_MODEL_INFO to get the modelname and type and prints an infobox.  
