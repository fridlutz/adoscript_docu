---
layout: commandcall
category: CommandCall
title: "GET_SELECTED"
tags: 1.3 1.5
---

GET_SELECTED returns the IDs of the currently selected objects in a model.

# Syntax:  

```adoscript
{% raw %}
CC "Modeling" GET_SELECTED  [ modelid:id ] .


# --> RESULT ecode:intValue objids:strValue classid:id .

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|id|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`objids`|strValue|
|`classid`|id|

# Remarks:

If modelid is not specified, the currently active model is used. The return value objids contains the IDs of the selected objects. If the model window is in "tabular modeling" mode and not in "overview" mode, the return value classid is the ID of the currently active class. Otherwise this value is 0.

Example:  
![](/images/DESELECT.png)

Activity "aktiv6" is selected, "aktiv5" is not.

Hint: does not work for tabular modeling.

# See Also:  



Example:




