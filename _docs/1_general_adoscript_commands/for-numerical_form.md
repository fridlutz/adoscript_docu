---
layout: commandcall
category: CommandCall
title: "FOR-numerical form"
tags: 1.3 1.5
---

FOR repeats a statement sequence for a variable running from one value to another.

# Syntax:  

```adoscript
{% raw %}
FOR varName from:numExpr to:numExpr [ by:numExpr ] { 
	StatementSequence 
}
{% endraw %}
```
{: .line-numbers}

# Parameters:

|`<main_parameter>`|varName, the name of the running variable|
|`from`|intValue, the start value for the running variable|
|`to`|intValue, the end value for the running variable|
|`by`|intValue, the size of the increment; if not specified, the running variable is incremented by 1.|

# Returns:



# Remarks:

At first the value of the from expression is assigned to the variable with the given name and the statement sequence is executed. The variable can be used in expressions in the statement sequence. After this first execution of the statement sequence the variable is incremented by the value specified with by or by 1 if by is not specified and the statement sequence is executed again. This is repeated while the value of the running variable is less or equal the specified to value.

# See Also:

[FOR-string token form](for-string_token_form.html "FOR-string token form")  
[WHILE](while.html "WHILE")  
[BREAK](break.html "BREAK")  


