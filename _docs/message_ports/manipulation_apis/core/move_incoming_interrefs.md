---
layout: commandcall
category: CommandCall
title: "MOVE_INCOMING_INTERREFS"
tags: 1.3 1.5
---

MOVE_INCOMING_INTERREFS changes the to-endpoint of incoming INTERREFs of one target object to another target object.

# Syntax:  

```adoscript
{% raw %}
CC "Core" MOVE_INCOMING_INTERREFS fromobjid:id toobjid:id .


#-->RESULT ecode:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`fromobjid`|id|
|`toobjid`|id|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|

# Remarks:



# See Also:  



Example:

