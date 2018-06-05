---
layout: commandcall
category: CommandCall
title: "SET_OUT_MAX_LINE_COUNT"
tags: 1.3 1.5
---

SET_OUT_MAX_LINE_COUNT sets the maximum line count of output text fields  (OUT). If more than the specified number of lines are appended, lines are deleted from the beginning to keep the maximum line count.

# Syntax:  

```adoscript
{% raw %}
CC "AdoScript" SET_OUT_MAX_LINE_COUNT intValue

# --> RESULT ecode:intValue .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`<main parameter>`|intValue, sets maximum line count (integer)|

# Returns:  

|`ecode`|intValue, error code if an error occured or 0 otherwise.|

# Remarks:



# See Also:  



Example:

