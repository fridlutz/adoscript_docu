---
layout: commandcall
category: CommandCall
title: "MOVE_MODEL_INCOMING_INTERREFS_IGNORE_NONMOVABLE"
tags: 1.3 1.5
---

MOVE_MODEL_INCOMING_INTERREFS_IGNORE_NONMOVABLE moves all the movable interrefs from one model to another.

# Syntax:  

```adoscript
{% raw %}
CC "Core" MOVE_MODEL_INCOMING_INTERREFS_IGNORE_NONMOVABLE frommodelid:intValue tomodelid:intValue .


#-->RESULT ecode:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`frommodelid`|intValue, the frommodelid, is the model ID of the source of the “to be moved” interrefs.|
|`tomodelid`|intValue, the tomodelid, is the model ID of the target of the “to be moved” interrefs.|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|

# Remarks:

Both models must be loaded and of the same type for this command to move the interrefs from the frommodelid to the tomodelid.

Non movable interrefs are those interrefs that have no corresponding object in the “to” model, that the original interref in the “from” model can attach too. This could happen for instance in a release workflow update where a model has been updated and an object removed that in the original model had an interref.

The message port command will leave unmovable interrefs behind, it will not delete or report non moveable interrefs. Before or after using this command it may be usefull to use the corresponding command QUERY_NON_MOVABLE_MODEL_INCOMING_INTERREFS which gives a list of all the non moveable interrefs. This can be used to allow the non movable interrefs to be processed separately i.e. deleted, or manually altered etc.

# See Also:  



Example 1:

```adoscript
{% raw %}

# call MOVE_MODEL_INCOMING_INTERREFS_IGNORE_NONMOVABLE
CC "Core" MOVE_MODEL_INCOMING_INTERREFS_IGNORE_NONMOVABLE frommodelid:(id1) tomodelid:(id2)

{% endraw %}
```
{: .line-numbers}

