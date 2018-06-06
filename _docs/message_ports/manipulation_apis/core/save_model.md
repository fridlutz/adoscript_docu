---
layout: commandcall
category: CommandCall
title: "SAVE_MODEL"
tags: 1.3 1.5
---

SAVE_MODEL saves changes of a model into the database.

# Syntax:  

```adoscript
{% raw %}
CC "Core" SAVE_MODEL modelid:id [ update-sys-attrs[: 1|0] ] 

#-->RESULT ecode:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|intValue, the id of the model that should be saved|
|`update-sys-attrs`|intValue, by default, the model's system attributes "Last user" and "Date last changed" are updated. This can be switched off by setting update-sys-attr to 0.|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|

# Remarks:



# See Also:  



Example 1:

```adoscript
{% raw %}

CC "CoreUI" MODEL_SELECT_BOX
CC "Modeling" IS_OPENED modelid:(VAL modelids)
IF (isopened) {
   CC "AdoScript" ERRORBOX "Select a model that is not opened in the model editor!"
   EXIT
}
CC "Core" LOAD_MODEL modelid:(VAL modelids)
# here we can access and change model information with Core commands,
# e.g. create a new instance
CC "Core" GET_CLASS_ID classname:"Aktivit�t"
IF (ecode != 0) {
   CC "AdoScript" ERRORBOX ("Your library does not contain a class " +
                            "called Aktivit�t!\n")
   EXIT
}
CC "Core" CREATE_OBJ modelid:(VAL modelids) classid:(classid)
                     objname:"A new activity"
IF (ecode != 0) {
    CC "AdoScript" ERRORBOX ("The object could not be created. \n" +
                             "Maybe one with the same name already exists?")
}
CC "Core" SAVE_MODEL modelid:(VAL modelids)
CC "Core" DISCARD_MODEL modelid:(VAL modelids)

{% endraw %}
```
{: .line-numbers}

Lets the user select a model, loads the model to the core, creates a new activity. Finally saves and then discards the model again.

Make sure that the model you select is closed and does not yet contain an activity called "A new activity". After executing the script, open the model.  
