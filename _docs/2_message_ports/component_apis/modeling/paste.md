---
layout: commandcall
category: CommandCall
title: "PASTE"
tags: 1.3 1.5
---

PASTE pastes all objects from the ADOxx internal clipboard into the specified model (modelid) at the coordinates x and y.

# Syntax:  

```adoscript
{% raw %}
CC "Modeling" PASTE [ modelid:modelId ] x:measureValue y:measureValue .


# --> RESULT ecode:intValue pastedobjids:strValue pastedrelnids:strValue .

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|modelId|
|`x`|measureValue|
|`y`|measureValue|

# Returns:  

|`ecode`|intValue, the return value ecode is set to 0 if pasting was successful, or to 1 if an error occured.|
|`pastedobjids`|strValue, IDs of pasted objects and connectors.|
|`pastedrelnids`|strValue, IDs of pasted connectors.|

# Remarks:

If no modelid is passed, the current active model is taken.


# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Modeling" SELECT_ALL
CC "Modeling" COPY_SELECTED
CC "Modeling" PASTE x:1cm y:15cm

{% endraw %}
```
{: .line-numbers}
Copies and pastes all objects in the currentlyactive model.

