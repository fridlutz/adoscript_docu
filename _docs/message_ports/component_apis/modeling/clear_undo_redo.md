---
layout: commandcall
category: CommandCall
title: "CLEAR_UNDO_REDO"
tags: 1.3 1.5
---

CLEAR_UNDO_REDO clears all actions in a model window's undo/redo manager.

# Syntax:  

```adoscript
{% raw %}
CC "Modeling" CLEAR_UNDO_REDO modelid:intValue
{% endraw %}
```
{: .line-numbers}


# Parameters:  

|`modelid`|intValue|

# Returns:  

none

# Remarks:

When a model is changed by an AdoScript, the current undo/redo status of that model is no longer up-to-date. When CC "Core" SET_ATTR_VAL is called, the undo/redo status of the changed model is cleared automatically. This covers most cases.  
This command has to be called when the undo/redo status shall be cleared in a context where SET_ATTR_VAL is not being called.

# See Also:  



Example:




