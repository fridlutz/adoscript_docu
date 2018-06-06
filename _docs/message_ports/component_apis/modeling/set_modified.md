---
layout: commandcall
category: CommandCall
title: "SET_MODIFIED"
tags: 1.3 1.5
---

SET_MODIFIED marks a model as modified (or unmodified).

# Syntax:  

```adoscript
{% raw %}
SetModelModified :	SET_MODIFIED [ id ] [ modified:intValue ] .

{% endraw %}
```
{: .line-numbers}


# Parameters:  

|`id`|modifier|
|`modified`|intValue|

# Returns:  

none

# Remarks:

If the user tries to close a modified model he is asked if he wants to save the changes.  
The ID of the model that shall be set as modified is passed via the nameless parameter. If no model ID is specified, the currently active model window is used.  
If modified is specified with value 0, the model is marked as not modified. In any other case (not specified, or specified with non-zero value) the model is marked as modified.

# See Also:  



Example:




