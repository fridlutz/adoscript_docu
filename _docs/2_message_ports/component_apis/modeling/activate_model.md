---
layout: commandcall
category: CommandCall
title: "ACTIVATE_MODEL"
tags: 1.3 1.5
---

ACTIVATE_MODEL activates a model. The activate model is displayed at top level in the model editor. If it was minimized, its model window is restored. The model id for the model that should be activated modified is passed in intVal.

# Syntax:  

```adoscript
{% raw %}
CC "Modeling" ACTIVATE_MODEL intValue
{% endraw %}
```
{: .line-numbers}


# Parameters:  

|`<main-parameter>`|intValue, ID of model|

# Returns:  

none

# Remarks:



# See Also:  



Example 1:

```adoscript
{% raw %}

CC "CoreUI" MODEL_SELECT_BOX 
CC "Modeling" IS_OPENED modelid:(VAL modelids)
IF (isopened = 1)
{
   CC "Modeling" ACTIVATE_MODEL (VAL modelids)
}

{% endraw %}
```
{: .line-numbers}
Lets the user select a model. If the model is currently opened, activate it.

