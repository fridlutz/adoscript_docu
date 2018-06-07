---
layout: commandcall
category: CommandCall
title: "GET_ALL_REFERENCED_MODELS_DB"
tags: 1.3 1.5
---

GET_ALL_REFERENCED_MODELS_DB returns a list of all model IDs (modelids) which are referenced by the source model specified by the parameter modelid  
(i.e. all outgoing references).

# Syntax:  

```adoscript
{% raw %}
CC "DB" GET_ALL_REFERENCED_MODELS_DB modelid:intValue 

#--> RESULT ecode:intValue modelids:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|intValue, ID of the model|

# Returns:  

|`ecode`|intValue, 0 if everything went ok != 0 otherwise.|
|`modelids`|strValue, a list of IDs separated by blanks (e.g. "10001 12345 4711").|

# Remarks:

This includes also references originating from attribute profiles used from within the source model and references originating from records.

# See Also:

