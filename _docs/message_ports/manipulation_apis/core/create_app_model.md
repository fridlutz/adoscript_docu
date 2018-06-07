---
layout: commandcall
category: CommandCall
title: "CREATE_APP_MODEL"
tags: 1.3 1.5
---

CREATE_APP_MODEL creates a new application model

# Syntax:  

```adoscript
{% raw %}
CC "Core" CREATE_APP_MODEL strValue bpmodelids:strValue wemodelid:id [points-on-thread].
{% endraw %}
```
{: .line-numbers}


# Parameters:  

|`<main_parameter>`|strValue, the name of the application model|
|`bpmodelids`|strValue, a list of model IDs defined in the ADOxx dynamic library|
|`wemodelid`|intValue, the ID of a model defined in the ADOxx static library|
|`points-on-thread`|modifier, may only be specified if you have a versioned application library. It determines whether your application model should point to a modelthread or to a specific model version.|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`appmodelid `|intValue, contains the id of the newly created application model.|

# Remarks:



# See Also:  



