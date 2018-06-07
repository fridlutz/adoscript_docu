---
layout: commandcall
category: CommandCall
title: "GET_AUTOSAVE"
tags: 1.3 1.5
---

GET_AUTOSAVE is used to retrieve the current autosave settings.

# Syntax:  

```adoscript
{% raw %}
CC "Modeling" GET_AUTOSAVE .


# --> RESULT enabled:boolValue changes:intValue

{% endraw %}
```
{: .line-numbers}

# Parameters:  

none

# Returns:  

|`enabled`|boolValue|
|`changes`|intValue|

# Remarks:

The user can change the autosave settings in the dialog "Automatic saving" in the menu "Extra":

![](/images/GET_AUTOSAVE.png)

When autosave is turned on, the return variable enabled is set to 1, if not it is set to 0. The return variable changes contains the number of changes after which models are automatically saved.

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Modeling" GET_AUTOSAVE
IF (enabled = 0)
{
   CC "AdoScript" INFOBOX "Autosave is turned off!"
}
ELSE
{
   CC "AdoScript" INFOBOX ("Autosave is turned on, models are automatically saved after " + STR changes + " changes in the model.")
}


{% endraw %}
```
{: .line-numbers}
This example queries the current autosave settings of the user and prints an apropriate message.

