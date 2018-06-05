---
layout: commandcall
category: CommandCall
title: "CLOSE (Modeling)"
tags: 1.3 1.5
---

CLOSE closes the model with the id modelid in the modeleditor.

# Syntax:  

```adoscript
{% raw %}
CC "Modeling" CLOSE [ modelid:intValue ] [ quiet [ save ] ].
{% endraw %}
```
{: .line-numbers}


# Parameters:  

|`modelid`|intValue|
|`quiet`|modifier|
|`save`|modifier|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|


# Remarks:

If no modelid is passed, the current active model will be taken.

When passing the argument quiet, the user will not be asked for models with unsaved changes if he wants to save them. The models will be closed and the changes discarded. For models that have been newly created without adding any objects and saving, the user will also not be asked if he wants to delete the model again, the model will just be closed, not deleted.  
If additional passing the argument save the model will also be saved.

The return variable ecode is set to 0 if closing worked, to 1 if an error occured.

ATTENTION:  
Closing the own model window is impossible when running in a PROGRAMCALL script which has been called by the user via the notebook or via the drawing area.

# See Also:  



Example 1:

```adoscript
{% raw %}

SEND "GET_ACTIVE_MODEL" to:"Modeling" answer:modelid
CC "Modeling" CLOSE modelid:(VAL modelid)

{% endraw %}
```
{: .line-numbers}
Closes the currently active model.

