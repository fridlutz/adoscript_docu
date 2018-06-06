---
layout: commandcall
category: CommandCall
title: "GET_CONNECTOR_ENDPOINTS"
tags: 1.3 1.5
---

GET_CONNECTOR_ENDPOINTS returns the ids of the instances that are connected by a connector.

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_CONNECTOR_ENDPOINTS objid:id .


#-->RESULT ecode:intValue fromobjid:id toobjid:id
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`objid`|id, The id of the connector is passed in the argument objid.|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`fromobjid`|id|
|`toobjid`|id|

# Remarks:

The return variable fromobjid is set to the id of the instance from which the connector is pointing and toobjid is set to the id of the instance to which the connector is poining.

# See Also:  



Example 1:

```adoscript
{% raw %}

# get all selected objects
CC "Modeling" GET_SELECTED
IF (objids = "")
{
   CC "AdoScript" ERRORBOX "Select a connector first!"
   EXIT
}

# from the list of selected objects, extract the first objectid
SET firstselected:(token(objids,0," "))

# now the all from and to instance
CC "Core" GET_CONNECTOR_ENDPOINTS objid:(VAL firstselected)
IF (ecode != 0)
{
   CC "AdoScript" ERRORBOX "Select a connector first!"
   EXIT
}

# now get the classes of the connected instances
CC "Core" GET_CLASS_ID objid:(fromobjid)
SET fromclassid:(classid)
CC "Core" GET_CLASS_ID objid:(toobjid)
SET toclassid:(classid)

# now get the names of the classes
CC "Core" GET_CLASS_NAME classid:(fromclassid)
SET fromclassname:(classname)
CC "Core" GET_CLASS_NAME classid:(toclassid)
SET toclassname:(classname)

# display the result
CC "AdoScript" INFOBOX ("You connected a " + fromclassname + " with a " + toclassname + ".")

{% endraw %}
```
{: .line-numbers}
The user has to select a connector before he starts the script. In the script, first the id of the selected connector is retrieved. With this id, the instances connected by the selected connector are retrieved with GET_CONNECTOR_ENDPOINTS. The ids of the from- and of the to-instance are returned. The classes and the classnames of the connected instances are computed and a message is displayed, telling the user which classes he connected.  
