---
layout: commandcall
category: CommandCall
title: "WHILE"
tags: 1.3 1.5
---

With WHILE a conditional loop can be programmed. At first the entry condition is evaluated.

# Syntax:  

```adoscript
{% raw %}
WHILE booleanExpr { 
	StatementSequence 
} 
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`<main_parameter>`|booleanExpr, evaluated after each loop|

# Returns:  



# Remarks:

If its value is non zero the following statement sequence is executed. Otherwise the running of the AdoScript is continued with the next element (following the closing curly brace of the WHILE element). After the statement sequence has been executed the WHILE condition is evaluated again and so on.

# See Also:  

[FOR-string token form](for-string_token_form.html "FOR-string token form")  
[FOR-numerical form](for-numerical_form.html "FOR-numerical form")  
[BREAK](break.html "BREAK")  


