---
layout: commandcall
category: CommandCall
title: "IS_OPENED"
tags: 1.3 1.5
---

S_OPENED checks if the model with the id modelid is already opened in the model editor.

# Syntax:  

```adoscript
{% raw %}
IsModelOpen :	IS_OPENED modelid:intValue .


# --> RESULT isopened:intValue

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|intValue|

# Returns:  

|`isopened`|intValue, the return variable isopened is set to 1 if the model is already opened, to 0 if it is not.|

# Remarks:



# See Also:  



Example 1:

```adoscript
{% raw %}

CC "CoreUI" MODEL_SELECT_BOX 
CC "Modeling" IS_OPENED modelid:(VAL modelids)
IF (isopened = 1)
{
   CC "AdoScript" INFOBOX "The model you selected is currently opened"
}
ELSE
{
   CC "AdoScript" INFOBOX "The model you selected is not opened yet"
}

{% endraw %}
```
{: .line-numbers}
Lets the user select a model in a model select box. Then checks if the model is currently open and prints an accordnig infobox.

