---
layout: commandcall
category: CommandCall
title: "SET_NOTEBOOK_POS"
tags: 1.3 1.5
---

SET_NOTEBOOK_POS sets the position of the notebook with the passed objid.

# Syntax:  

```adoscript
{% raw %}
CC "Modeling" SET_NOTEBOOK_POS objid:intValue x:intValue y:intValue .


# --> RESULT ecode:intValue

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`objid`|intValue|
|`x`|intValue|
|`y`|intValue|

# Returns:  

|`ecode`|intValue, the return variable ecode is set to 0 if setting worked, to 1 if an error occured.|


# Remarks:

The passed x and y values are pixel.



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
CC "Modeling" SET_NOTEBOOK_POS objid:(myObjId) x:(0) y:(0)
CC "Application" GET_SCREEN_RES
CC "Modeling" SET_NOTEBOOK_SIZE objid:(myObjId) w:(w) h:(h)
CC "AdoScript" INFOBOX "Now one notebook in the model should be executed and fit the whole screen!"
CC "Modeling" CLOSE_ALL_NOTEBOOKS modelid:(VAL modelid)

{% endraw %}
```
{: .line-numbers}
Executes the notebook of the first object in the currently active model and set the position and the size to fit the whole screen.  
After displaying an infobox so that the user can see the notebook all notebooks are closed again.

