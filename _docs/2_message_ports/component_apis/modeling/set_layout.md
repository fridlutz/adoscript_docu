---
layout: commandcall
category: CommandCall
title: "SET_LAYOUT"
tags: 1.3 1.5
---

SET_LAYOUT sets the current page layout of a model.

# Syntax:  

```adoscript
{% raw %}
CC "Modeling" SET_LAYOUT [ id | modelid:id ] 
						 [ layout:strValue ] 
						 [ orientation:Orientation ]
						 [ Scaling ]   .


Scaling :	factor:intValue |
fitonepage |
pages-height:intValue |
pages-width:intValue .


Orientation :	"automatically" | "portrait" | "landscape" .


# --> RESULT ecode:intValue .

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`id`|modifier|
|`modelid`|id|
|`layout`|strValue|
|`orientation`|Orientation|
|`factor`|intValue|
|`fitonepage`|modifier|
|`pages-height`|intValue|
|`pages-width`|intValue|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|


# Remarks:

By now there is no corresponding read command, but the reading the page layout status can therefore be done via the page layout model attribute.

# See Also:  



Example:



