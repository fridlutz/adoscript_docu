---
layout: commandcall
category: CommandCall
title: "GET_REPRESENTATION"
tags: 1.3 1.5
---

GET_REPRESENTATION returns the representation mode (graphical or tabular) in wich a model is currently displayed in a model window.

# Syntax:  

```adoscript
{% raw %}
CC "Modeling" GET_REPRESENTATION [ modelid:id ] .


# --> RESULT ecode:intValue representation:Representation[ classid:id ] .
Representation : "graphical" | "tabular" .

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|id|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`representation`|Representation|
|`classid`|id|

# Remarks:

If no modelid is specified, the currently active model is used.

If representation is "tabular", classid is the ID of the active classs. A classid value of 0 in tabular representation means "overview representation".

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Modeling" GET_REPRESENTATION modelid:(modelid)

{% endraw %}
```
{: .line-numbers}


