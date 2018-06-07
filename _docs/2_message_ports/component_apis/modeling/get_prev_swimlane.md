---
layout: commandcall
category: CommandCall
title: "GET_PREV_SWIMLANE"
tags: 1.3 1.5
---

GET_PREV_SWIMLANE returns the object ID of the previous swimlane for the swimlane with the given object ID. For a horizontal swimlane this is the next swimlane above, for vertical swimlanes the next swimlane on the left-hand side.

# Syntax:  

```adoscript
{% raw %}
CC "Modeling" GET_PREV_SWIMLANE objid:intValue .


# --> RESULT ecode:intValue objid:intValue

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`objid`|intValue|

# Returns:  

|`ecode`|intValue, contains the error code or is 0 in case of success.|
|`objid`|intValue, a result objid of 0 means that the given swimlane is the first one in the model.|

# Remarks:



# See Also:  

[GET_NEXT_SWIMLANE](get_next_swimlane.html "GET_NEXT_SWIMLANE")  


Example 1:

```adoscript
{% raw %}

CC "Modeling" GET_PREV_SWIMLANE

{% endraw %}
```
{: .line-numbers}


