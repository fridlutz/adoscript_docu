---
layout: commandcall
category: CommandCall
title: "UPDATE_ALL_EXPR_ATTRS"
tags: 1.3 1.5
---

The command UPDATE_ALL_EXPR_ATTRS forces alle expression attributes of all loaded models to be updated.

# Syntax:  

```adoscript
{% raw %}
CC "Core" UPDATE_ALL_EXPR_ATTRS [synchronous:int]
{% endraw %}
```
{: .line-numbers}


# Parameters:  

|`synchronous`|int|

# Returns:  

none

# Remarks:

With the optional parameter synchronous you can toggle, whether the expressions should be updated right now (if the value is not 0) or if it should take place while you are working (value: 0).

# See Also:  



Example 1:

```adoscript
{% raw %}

# update all expression attributes
CC "Core" UPDATE_ALL_EXPR_ATTRS synchronous:1

CC "AdoScript" INFOBOX ("All expression attributes have been updated!")

{% endraw %}
```
{: .line-numbers}

