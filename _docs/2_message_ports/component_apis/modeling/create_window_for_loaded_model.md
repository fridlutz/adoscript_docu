---
layout: commandcall
category: CommandCall
title: "CREATE_WINDOW_FOR_LOADED_MODEL"
tags: 1.3 1.5
---

With the command CREATE_WINDOW_FOR_LOADED_MODEL, a model that has already been loaded in the core can be made visible in the model editor.

# Syntax:  

```adoscript
{% raw %}
CC "Modeling" CREATE_WINDOW_FOR_LOADED_MODEL modelid:intValue .


# --> RESULT ecode:intValue

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|intValue|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|

# Remarks:

Models loaded with the command LOAD_MODEL of the Core Messageport are not visible on the user interface.

The return variable ecode returns the value 0 if the command was successful, -1 if not.


# See Also:  



Example 1:

```adoscript
{% raw %}

CC "CoreUI" MODEL_SELECT_BOX 
CC "Core" LOAD_MODEL modelid:(VAL modelids)
CC "AdoScript" INFOBOX "Now the model is loaded but not visible..."
CC "Modeling" CREATE_WINDOW_FOR_LOADED_MODEL modelid:(VAL modelids)
CC "AdoScript" INFOBOX "Now the model is loaded and opened in the modeleditor."

{% endraw %}
```
{: .line-numbers}
This example lets the user select a model. First the model is loaded in the core. After that the model is not visible in the modeleditor but can be edited with adoscript commands. After displaying an infobox, the loaded model is opened in the model editor.

