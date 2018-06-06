---
layout: commandcall
category: CommandCall
title: "SHOW_NOTEBOOK_CHAPTER"
tags: 1.3 1.5
---

SHOW_NOTEBOOK_CHAPTER shows a chapter and the chapter-page in an executed notebook of the passed objid.  


# Syntax:  

```adoscript
{% raw %}
CC "Modeling" SHOW_NOTEBOOK_CHAPTER objid:intValue chapter:intValue chapter-page:intValue.


# --> RESULT ecode:intValue

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`objid`|intValue|
|`chapter`|intValue|
|`chapter-page`|intValue.|

# Returns:  

|`ecode`|intValue, the return variable ecode is set to 0 if showing worked, to 1 if an error occured.|


# Remarks:

Attention:  
This command does not work for model notebooks!

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

CC "Modeling" EXEC_NOTEBOOK objid:(VAL token(objids,1," "))

CC "Modeling" SHOW_NOTEBOOK_CHAPTER objid:(VAL token(objids,1," ")) chapter:1 chapter-page:2
CC "AdoScript" INFOBOX "Now one notebook in the model should be executed and the second page of the first chapter should be shown!"
CC "Modeling" CLOSE_ALL_NOTEBOOKS modelid:(VAL modelid)

{% endraw %}
```
{: .line-numbers}
Executes the notebook of the first object in the currently active model and shows the second page of the first chapter. After displaying an infobox so that the user can see the notebook all notebooks are closed again.

