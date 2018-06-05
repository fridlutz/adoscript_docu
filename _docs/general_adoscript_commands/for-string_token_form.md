---
layout: commandcall
category: CommandCall
title: "FOR-string token form"
tags: 1.3 1.5
---

This version of **FOR** repeats a statement sequence for a variable running through a sequence of tokens.  


# Syntax:  

```adoscript
{% raw %}
FOR varName in:strExpr [ sep:strExpr ] { 
	StatementSequence 
}
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`<main_parameter>`|varName, the name of the running variable|
|`in`|strExpr, the sequence of tokens; the domain of the running variable|
|`sep`|strExpr, the character that separates the tokens inside the sequence; default " "|

# Returns:  

none

# Remarks:

The token sequence is specified with **in**. Optionally a separator can be specified with  
*sep* which is the space character (" ") by default.

# See Also:  

[FOR-numerical form](for-numerical_form.html "FOR-numerical form")  
[WHILE](while.html "WHILE")  
[BREAK](break.html "BREAK")  


Example 1:

After executing the code  
```adoscript
{% raw %}

SET result:0
FOR ei in:"12 23 34" {
  SET result:(result + VAL ei)
}

{% endraw %}
```
{: .line-numbers}
*result* has the value *69*. Notice that *VAL* is needed to transform the string value of *ei* to an integer value.

