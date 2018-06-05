---
layout: commandcall
category: CommandCall
title: "SAVE_LIBRARY"
tags: 1.3 1.5
---

SAVE_LIBRARY saves changes in a library to the database.

# Syntax:  

```adoscript
{% raw %}
CC "Core" SAVE_LIBRARY libid:intValue

#--> RESULT ecode:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`libid`|intValue, the id of the library|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|

# Remarks:

This may be required when altering attribute profiles!

# See Also:  



