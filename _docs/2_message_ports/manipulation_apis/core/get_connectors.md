---
layout: commandcall
category: CommandCall
title: "GET_CONNECTORS"
tags: 1.3 1.5
---

GET_CONNECTORS returns a list of all object ids (separated by spaces) of connectors leading from or to one object.

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_CONNECTORS objid:id [ in ] [ out ] .


#-->RESULT ecode:intValue objids:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`objid`|id, the id of the object is specified with the argument objid.|
|`in`|modifier|
|`out`|modifier|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`objids`|strValue, the list of objects is returned in the variable objids.|

# Remarks:

When no further arguments are passed, incoming (leading to the object) and outgoing (leading from the object) connectors are evaluated. When the argument in is passed, only incoming connectors are returned. When the argument out is passed, only outgoing connectors are returned.


# See Also:  



Example 1:

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

# now get all incoming connectors
CC "Core" GET_CONNECTORS objid:(VAL firstselected) in

# for each connecor, dye it
FOR id in:(objids)
{
   CC "Modeling" DYE (VAL id) error-mark
}

{% endraw %}
```
{: .line-numbers}
Retrieves the ids of the currently selected object. Calls GET_CONNECTORS to compute all incoming connectors to this object. In a for loop dyes each found connector.

Hint: If you are not interested in the attached connectors, but in the objects which are related by a certain connector class (e.g. "Nachfolger"), you could call  
CC "Core" EVAL_EXPRESSION (ctobjs(objid, "Nachfolger"))  
instead of calling GET_ALL_CONNECTORS and then GET_CONNECTOR_ENDPOINTS for each connector of the concerned connector class.  
