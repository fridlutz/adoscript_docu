---
layout: commandcall
category: CommandCall
title: "GET_MODEL_HIERARCHY"
tags: 1.3 1.5
---

GET_MODEL_HIERARCHY returns a submodel tree of a model as XML.

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_MODEL_HIERARCHY modelid:intValue 

#--> RESULT ecode:intValue hierarchy:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|intValue, ID of the root model|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`hierarchy`|strValue, has the same structure as the tree in the hierarchy explorer. For each model contained in the hierarchy the retured XML contains a &lt;model&gt; node with an id attribute. Direct submodels of a model are written as direct children of the related model tag in the XML.|

# Remarks:

When the hierarchy builder detects a cycle one model is visited which has already been visited in the path, the model closing the cycle is listed as leaf node.

# See Also:  



Example 1:

For a call  
```adoscript
{% raw %}

CC "Core" GET_MODEL_HIERARCHY modelid:16083

{% endraw %}
```
{: .line-numbers}

the result hierarchy could look like this  
```adoscript
{% raw %}
<?xml version="1.0" encoding="UTF-8"?>
<model id="16083">
  <model id="15918">
    <model id="15976">
      <model id="15918" />
    </model>
  </model>
  <model id="15976">
    <model id="15918">
      <model id="15976" />
    </model>
  </model>
</model>
{% endraw %}
```
{: .line-numbers}
