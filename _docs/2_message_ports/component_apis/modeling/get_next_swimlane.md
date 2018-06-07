---
layout: commandcall
category: CommandCall
title: "GET_NEXT_SWIMLANE"
tags: 1.3 1.5
---

GET_NEXT_SWIMLANE returns the object ID of the succeeding swimlane for the swimlane with the given object ID. For a horizontal swimlane this is the next swimlane below, for vertical swimlanes the next swimlane on the right-hand side.

# Syntax:  

```adoscript
{% raw %}
CC "Modeling" GET_NEXT_SWIMLANE objid:intValue

# --> RESULT ecode:intValue objid:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`objid`|intValue|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`objid`|intValue, a result objid of 0 means that the given swimlane is the last one in the model.|

# Remarks:




# See Also:  

[GET_PREV_SWIMLANE](get_prev_swimlane.html "GET_PREV_SWIMLANE")  


Example 1:

```adoscript
{% raw %}

CC "Modeling" GET_NEXT_SWIMLANE

{% endraw %}
```
{: .line-numbers}


