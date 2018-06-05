---
layout: commandcall
category: CommandCall
title: "GET_ALL_MODEL_VERSIONS"
tags: 1.3 1.5
---

GET_ALL_MODEL_VERSIONS returns a list of all model versions.

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_ALL_MODEL_VERSIONS 	[ modeltype:strValue ]
									[ only-write-access[: 1|0 ]]
									[ only-visible-models[: 1|0 ]].

#-->RESULT ecode:intValue modelversionids:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modeltype`|strValue, name of the model type; when present, only versions of this model type will be returned|
|`only-write-access`|1|0, when passed without value or with a 1 value, only those models are returned on which the user has write permission.|
|`only-visible-models`|1|0, when passed without value or with a "true" value, only those models are returned which are contained in at least one model group (i.e. models which are not contained in the "model pool"). By default, models of the "model pool" are contained in the result, although these models cannot be accessed via user interface in the ADOxx Modelling Toolkit.|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`modelversionids`|strValue, contains a list with all model versions (optionally filtered).|

# Remarks:

Optionally this list is filtered to only one modeltype and/or only write-access permitted models.

This command returns all versions, so multiple entries of the same model thread are possible (that means multiple versions of one thread!).

# See Also:  

[GET_ALL_MODEL_THREADS](get_all_model_threads.html "GET_ALL_MODEL_THREADS")  


Example 1:

Get all model versions of type "Sample Model"  
```adoscript
{% raw %}

CC "Core" GET_ALL_MODEL_VERSIONS modeltype:"Sample Model"
IF (ecode) {
    CC "AdoScript" ERRORBOX ("Error: " + STR ecode)
} ELSE {
    CC "AdoScript" INFOBOX ("Model version IDs: " + modelversionids)
}

{% endraw %}
```
{: .line-numbers}

