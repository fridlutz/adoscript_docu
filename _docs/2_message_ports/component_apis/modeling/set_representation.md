---
layout: commandcall
category: CommandCall
title: "SET_REPRESENTATION"
tags: 1.3 1.5
---

SET_REPRESENTATION sets the representation (graphical or tabular) in wich a model is displayed in a model window.  

# Syntax:  

```adoscript
{% raw %}
CC "Modeling" SET_REPRESENTATION	[ modelid:id ] representation:Representation
									[ classid:id ] .


Representation :	"graphical" | "tabular" .
{% endraw %}
```
{: .line-numbers}

```adoscript
{% raw %}
# --> RESULT ecode:intValue .

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|id|
|`representation`|Representation|
|`classid`|id|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|


# Remarks:

If no modelid is specified, the currently active model is used. If representation is set to "tabular", the displayed table can be set via classid. A classid value of 0 means "overview mode", not specifying classid means "show the table which has been visible at last".

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Modeling" SET_REPRESENTATION modelid:(modelid)
        representation:"tabular" classid:(classid)

{% endraw %}
```
{: .line-numbers}


