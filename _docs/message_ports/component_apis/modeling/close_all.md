---
layout: commandcall
category: CommandCall
title: "CLOSE_ALL"
tags: 1.3 1.5
---

CLOSE_ALL closes all currently opened model in the modeleditor.

# Syntax:  

```adoscript
{% raw %}
CC "Modeling" CLOSE_ALL [ quiet [ save ] ].


# --> RESULT ecode:intValue

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`quiet`|modifier|
|`save`|modifier|

# Returns:  

|`ecode`|intValue, the return variable ecode is set to 0 if closing worked, to 1 if an error occured.|


# Remarks:

When passing the argument quiet, the user will not be asked for models with unsaved changes if he wants to save them. The models will be closed and the changes discarded. For models that have been newly created without adding any objects and saving, the user will also not be asked if he wants to delete the model again, the model will just be closed, not deleted.  
If additional passing the argument save the model will also be saved.

ATTENTION:  
Closing the own model window is impossible when running in a PROGRAMCALL script which has been called by the user via the notebook or via the drawing area.

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Modeling" CLOSE_ALL


{% endraw %}
```
{: .line-numbers}
Closes all currently opened models.

