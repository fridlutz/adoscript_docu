---
layout: commandcall
category: CommandCall
title: "GET_ALL_MODEL_THREADS"
tags: 1.3 1.5
---

GET_ALL_MODEL_THREADS returns a list of all model threads.

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_ALL_MODEL_THREADS	[ modeltype:strValue ] [ only-write-access ] .

#-->RESULT ecode:intValue modelthreadids:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modeltype`|strValue, if passed, only model threads of this model type are returned|
|`only-write-access`|modifier, when passed, only threads of models are returned on which the user has write permission.|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`modelthreadids`|strValue, a list of the model thread IDs separated by blanks|

# Remarks:

Optionally this list is filtered to only one modeltype and/or only write-access permitted models.

This command returns only the thread ids of (filtered) models. Is a versionized application library is used and all versions are needed, use GET_ALL_MODEL_VERSIONS instead (see ).

# See Also:  

[GET_ALL_MODEL_VERSIONS](get_all_model_versions.html "GET_ALL_MODEL_VERSIONS")  


Example 1:

Get all model threads type "Sample Model"  
```adoscript
{% raw %}

CC "Core" GET_ALL_MODEL_THREADS modeltype:"Sample Model"
IF (ecode) {
    CC "AdoScript" ERRORBOX ("Error: " + STR ecode)
} ELSE {
    CC "AdoScript" INFOBOX ("Model thread IDs: " + modelthreadids)
}

{% endraw %}
```
{: .line-numbers}

