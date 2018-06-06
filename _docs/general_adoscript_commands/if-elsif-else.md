---
layout: commandcall
category: CommandCall
title: "IF - ELSIF - ELSE"
tags: 1.3 1.5
---

With IF a conditional branch can be programmed.

# Syntax:  

```adoscript
{% raw %}
IF booleanExpr {
	StatementSequence 
}
ELSIF booleanExpr { 
	StatementSequence 
}
ELSE { 
StatementSequence 
} 
{% endraw %}
```
{: .line-numbers}


# Parameters:  

|`<main_parameter>`|booleanExpr|

# Returns:  

none

# Remarks:

At first the IF conditions is evaluated. If its value is non zero the following statement sequence is executed. Otherwise if there is an ELSIF clause the belonging condition is evaluated in the same way and so on. If none of the IF/ELSIF conditions is evaluated to a non zero value the ELSE statement sequence is executed if there is one.

Any number of ELSIF blocks may be used, but at most one ELSE block may be used.

# See Also:  


