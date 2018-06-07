---
layout: event
category: Event
title: "OpenModel"
tags: 1.3 1.5
---

A model has been loaded. The ID of the model is assigned to the variable modelid.  

# Parameters:  

|`modelid`|intValue, the ID of the model|

Exit value:



# Remarks:  

The event is sent after the model has been loaded, but before a model window for that model is created.  

# See Also:  



Example:

```adoscript
{% raw %}

   ON_EVENT "OpenModel"�{
       CC "Core" EVAL_EXPRESSION (maval("Description")) modelid:(modelid)
    �  CC "AdoScript" INFOBOX (result)
  �}

{% endraw %}
```
{: .line-numbers}
displays the description of a model after it has been opened.

