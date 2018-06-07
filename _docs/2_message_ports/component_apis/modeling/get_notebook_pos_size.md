---
layout: commandcall
category: CommandCall
title: "GET_NOTEBOOK_POS_SIZE"
tags: 1.3 1.5
---

GET_NOTEBOOK_POS_SIZE returns the position x, y and the size w, h of the notebook with the passed objid in pixel.

# Syntax:  

```adoscript
{% raw %}
CC "Modeling" GET_NOTEBOOK_POS_SIZE objid:intValue  .


# --> RESULT ecode:intValue x:intValue y:intValue w:intValue h:intValue

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`objid`|intValue|

# Returns:  

|`ecode`|intValue, the return variable ecode is set to 0 if setting worked, to 1 if an error occured.|
|`x`|intValue|
|`y`|intValue|
|`w`|intValue|
|`h`|intValue|

# Remarks:



# See Also:  



Example 1:

```adoscript
{% raw %}

# get the current model
SEND "GET_ACTIVE_MODEL" to:"Modeling" answer:modelid
IF (modelid = "")
{
   CC "AdoScript" ERRORBOX "Open a model first!"
   EXIT
}

# get all objects
CC "Core" GET_ALL_OBJS modelid:(VAL modelid)
IF (ecode != 0)
{
   CC "AdoScript" ERRORBOX "Something went very wrong here (e.g. we passed the wrong model id)!\n"
   EXIT
}

SET myObjId:(VAL token(objids,1," "))

CC "Modeling" EXEC_NOTEBOOK objid:(myObjId)
CC "Modeling" debug GET_NOTEBOOK_POS_SIZE objid:(myObjId)
CC "Modeling" CLOSE_ALL_NOTEBOOKS modelid:(VAL modelid)

{% endraw %}
```
{: .line-numbers}
Shows the size of a notebook.

