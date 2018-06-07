---
layout: commandcall
category: CommandCall
title: "QUERY_NON_MOVABLE_MODEL_INCOMING_INTERREFS"
tags: 1.3 1.5
---

QUERY_NON_MOVABLE_MODEL_INCOMING_INTERREFS returns a list of non movable incoming interrefs from one model to another model.

# Syntax:  

```adoscript
{% raw %}
QueryNonMovableIncomingInterrefs :	QUERY_NON_MOVABLE_MODEL_INCOMING_INTERREFS frommodelid:intValue tomodelid:intValue .


#-->RESULT ecode:intValue reftext:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`frommodelid`|intValue, the frommodelid, is the model ID of the source of the “to be moved” interrefs.|
|`tomodelid`|intValue, the tomodelid, is the model ID of the target of the “to be moved” interrefs.|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`reftext`|strValue|

# Remarks:

Both models need to be loaded for the command to work correctly.


An example of use for this command is in version control. Detailed references of a model A1 will need to be moved on to the successor of the model A2 when A1 is approved, and a new version A2 comes along. A1 is moved into the archives and A2 becomes the new approved version. Thus all interrefs of A1 must now be attached to A2. Before such an action (A2 is released and A1 is archived) all interrefs need to be checked to see if they can really be shifted from A1 to A2. If an object in A2 does not exist any longer and the user needs a warning, this message port is very useful as it returns a list of non movable interrefs.

If there are no non movable interrefs then the returned list will be empty.  
If reftext is not empty, it contains 1 to n lines of the following code (each line describing one interref).

REF srcmodelid - intValue  
srcdobjid - intValue  
srcattrid - intValue  
srcobjname - strValue  
srcownerid - intValue  
srcownerattrid - intValue  
targettype - modifier  
tmodeltype - strValue  
tmodelname - strValue  
tversion - strValue  
tclassname - strValue  
tobjname - strValue '\n'

targettype is either the modifier "model" or "object" depending on whether you have a reference to a model (model reference) or a reference to an object in a model (instance reference).  
If srcobjid and srcownerid (and srcattrid and srcownerattrid) contain the same ID, then the reference comes from a modeling instance (with ID scrobjid in model srcmodelid).  
If the reference originated from a recordrow, then srcobjid will be the ID of the record row and srcattrid will be the ID of the column within the record.  
In this case the owner of the record row (the modeling instance) will be given by srcownerid, and scrownerattrid is the ID of the record attribute.  
Note:  
In both cases srcobjname will contain the name of the modeling instance!

The target of the reference is given by tmodeltype, tmodelname, tversion, tclassname, and tobjname.  
If targettype is "model" you can ignore the variables tclassname and tobjname since they always contain an empty string ("").

# See Also:  



Example 1:

```adoscript
{% raw %}

# call QUERY_NON_MOVABLE_MODEL_INCOMING_INTERREFS
CC "Core" QUERY_NON_MOVABLE_MODEL_INCOMING_INTERREFS frommodelid:(id1) tomodelid:(id2)

{% endraw %}
```
{: .line-numbers}

