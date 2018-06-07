---
layout: commandcall
category: CommandCall
title: "LOAD_MODEL"
tags: 1.3 1.5
---

LOAD_MODEL loads a model from the database to the Core. The loaded model is not displayed in the model editor. To load a model in the model editor, use the Modeling command OPEN.

# Syntax:  

```adoscript
{% raw %}
CC "Core" LOAD_MODEL modelid:intValue [ read-access ]

#-->RESULT ecode:intValue isloaded:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|intValue, the id of the model that should be loaded|
|`read-access`|modifier, when passed, the model is loaded with read-only access. Model information can then only be read, not changed.|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`isloaded`|intValue, specifies whether the model has been loaded or not; it is set to 1 if the model could be loaded or 0 otherwise.|

# Remarks:

Every model which is created or loaded via the "Core" MessagePort has to be discarded using DISCARD_MODEL or opened in the model editor with CREATE_WINDOW_FOR_LOADED_MODEL.If it is not discarded, the user will not be able to open it later in the model editor.

The return variable ecode does not tell if the model is loaded or not. It can be set to a value different then 0 and the model can still be loaded. E.g. ecode is different from 0 when the model should be loaded with write access but could only be loaded with read access. If the ecode ACCESSMODE_CHANGED (72) is returned the model is loaded but read-only.

Do not confuse with CC "Modeling" OPEN! "LOAD_MODEL" loads the model only into the Core, use OPEN if you want to display the model (which costs performance due graphicoverhead.)  

# See Also:  

[OPEN](open.html "OPEN")  
[DISCARD_MODEL](discard_model.html "DISCARD_MODEL")  
[CREATE_WINDOW_FOR_LOADED_MODEL](create_window_for_loaded_model.html "CREATE_WINDOW_FOR_LOADED_MODEL")  


Example 1:

```adoscript
{% raw %}

CC "CoreUI" MODEL_SELECT_BOX 

CC "Core" LOAD_MODEL modelid:(VAL modelids)

CC "AdoScript" INFOBOX "Now the model is loaded but not visible..."
# here we can access model information with Core commands

CC "Core" DISCARD_MODEL modelid:(VAL modelids)


{% endraw %}
```
{: .line-numbers}
Lets the user select a model. Loads the model to the core and then discards the model again.

