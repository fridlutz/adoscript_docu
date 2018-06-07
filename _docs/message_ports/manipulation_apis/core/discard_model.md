---
layout: commandcall
category: CommandCall
title: "DISCARD_MODEL"
tags: 1.3 1.5
---

DISCARD_MODEL removes a model that has previously been loaded with &lt;LOAD_MODEL&gt; from the core.

# Syntax:  

```adoscript
{% raw %}
CC "Core" DISCARD_MODEL modelid:id

#-->RESULT ecode:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|intValue, the id of the model that should be loaded|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|

# Remarks:

All changes that have been made to the model since it was loaded are lost unless they are saved to the database with &lt;SAVE_MODEL&gt; prior to calling DISCARD_MODEL.

Every model which is created or loaded via the "Core" MessagePort has to be discarded using DISCARD_MODEL or opened in the model editor with CREATE_WINDOW_FOR_LOADED_MODEL. If it is not discarded, the user will not be able to open it later in the model editor.

Models that have been opened in the model editor must not be closed with the DISCARD_MODEL command. Use the "Modeling" MessagePort command CLOSE instead.

# See Also:  

[LOAD_MODEL](load_model.html "LOAD_MODEL")  
[SAVE_MODEL](save_model.html "SAVE_MODEL")  
[CREATE_WINDOW_FOR_LOADED_MODEL](create_window_for_loaded_model.html "CREATE_WINDOW_FOR_LOADED_MODEL")  
[CLOSE](close.html "CLOSE")  


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
