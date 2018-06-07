---
layout: commandcall
category: CommandCall
title: "CHECK_AQL_EXPRESSION"
tags: 1.3 1.5
---

CHECK_AQL_EXPRESSION will check the specified string according to the AQL syntax. No semantic check is done.

# Syntax:  

```adoscript
{% raw %}
CC "AQL" CHECK_AQL_EXPRESSION expr:strValue

# --> RESULT ecode:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`expr`|strValue|

# Returns:  

|`ecode`|intValue, is 0 if the expression is syntactically ok.|

# Remarks:



# See Also:  

[EVAL_AQL_EXPRESSION](eval_aql_expression.html "EVAL_AQL_EXPRESSION")  


