---
layout: commandcall
category: CommandCall
title: "CREATE_OBJ"
tags: 1.3 1.5
---

CREATE_OBJ creates a new instance of a certain class in a certain model. The model must be loaded.

# Syntax:  

```adoscript
{% raw %}
CC "Core" CREATE_OBJ modelid:intValue classid:intValue objname:strValue .


#-->RESULT ecode:intValue  objid:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|intValue, the ID of the model in which the object should be created|
|`classid`|intValue, he ID of the class of which an instance should be created|
|`objname`|strValue, the name of the instance|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`objid`|intValue, the ID of the new object.|

# Remarks:



# See Also:  



Example 1:

```adoscript
{% raw %}

# get the modelid of the current model
SEND "GET_ACTIVE_MODEL" to:"Modeling" answer:modelid
IF (modelid = "") {
    CC "AdoScript" ERRORBOX "Open a new model first!"
    EXIT
}

# get the id of class "Aktivität"
CC "Core" GET_CLASS_ID classname:"Aktivität"

# create the object
CC "Core" CREATE_OBJ modelid:(VAL modelid) classid:(classid) objname:"A new activity"
IF (ecode != 0) {
    CC "AdoScript" ERRORBOX ("The object could not be created. \n"+
                             "Maybe one with the same name already exists?")
}

# this has to be called to update the modeling window
CC "Modeling" REBUILD_DRAWING_AREA

{% endraw %}
```
{: .line-numbers}
Open a new model and execute the script. The script ascertains the ID of the class "Aktivität" and the ID of the active model. With these IDs it creates a new instance.

Example 2:

```adoscript
{% raw %}

CC "Modeling" GET_ACT_MODEL
SET classname:"Aktivität"  # name of the class of which objects are created here
SET n:999                  # number of objects to create
SET m:(INT(sqrt(n)))
CC "Core" GET_CLASS_ID classname:(classname)
SET newobjs:(array(0))
FOR i from:0 to:(n - 1) {
    CC "Core" CREATE_OBJ modelid:(modelid) classid:(classid)
            objname:(classname + STR i)
    SET dummy:(aappend(newobjs, objid))
    CC "Application" SET_STATUS ("Objekt erzeugt: " + STR (i + 1) + "/" + STR n)
}
CC "Modeling" REBUILD_DRAWING_AREA
FOR i from:0 to:(n - 1) {
    SET x:(2cm + (i - FLOOR(i / m) ** m) ** 4cm)
    SET y:(2cm + FLOOR(i / m) ** 4cm)
    CC "Modeling" SET_OBJ_POS objid:(newobjs[i]) x:(x) y:(y)
    CC "Application" SET_STATUS ("Objekt positioniert: " +
            STR (i + 1) + "/" + STR n)
}

{% endraw %}
```
{: .line-numbers}

