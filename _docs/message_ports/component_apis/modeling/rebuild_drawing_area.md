---
layout: commandcall
category: CommandCall
title: "REBUILD_DRAWING_AREA"
tags: 1.3 1.5
---

Some kinds of changes in the core are not recognized by the drawing area automatically. REBUILD_DRAWING_AREA brings the drawing area of the model with the given modelid into consistence with the model data held by the core.

# Syntax:  

```adoscript
{% raw %}
RebuildDrawingArea :	REBUILD_DRAWING_AREA [ modelid:id ] .

{% endraw %}
```
{: .line-numbers}


# Parameters:  

|`modelid`|id|

# Returns:  

none

# Remarks:

For models which are currently displayed in a model window, this command has to be called after new objects or connectors have been created via the "Core" message port.

# See Also:  



Example:




