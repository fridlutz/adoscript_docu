---
layout: commandcall
category: CommandCall
title: "EVAL_EXPRESSION"
tags: 1.3 1.5
---

The command EVAL_EXPRESSION evaluates a core expression without the need of an EXPRESSION attribute.

# Syntax:  

```adoscript
{% raw %}
CC "Core" EVAL_EXPRESSION coreExpr [ objid:intValue | modelid:intValue ]

#-->RESULT ecode:intValue result:value
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`<main_parameter`|coreExpr, is a string containing a core expression.|
|`objid`|intValue, id of an object if the expression is object-related|
|`modelid`|intValue, id of a model if the expression is model-related|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`result`|is the same type as the expression's result type and contains the expression's result. If the command failed result is of type STRING and contains an error message.|

# Remarks:

For mode details about expressions visit www.adoxx.org

# See Also:  



Example 1:

```adoscript
{% raw %}

# get all selected objects
CC "Modeling" GET_SELECTED
IF (objids = "")
{
   CC "AdoScript" ERRORBOX "Select an instance first!"
   EXIT
}

# from the list of selected objects, extract the first objectid
SET firstselected:(token(objids,0," "))

CC "Core" EVAL_EXPRESSION (aval("Double")**2 + aval("Integer")**3) objid:(VAL firstselected)

IF ((ecode)!=0)
{
  CC "AdoScript" ERRORBOX ("Error ("+(STR ecode)+"): "+result)
  EXIT
}

CC "AdoScript" INFOBOX ("Double**2 + Integer**3 = "+(STR result))

{% endraw %}
```
{: .line-numbers}

Preparing  
- Get selected objects  
- pick first selected

Interesting  
- EVAL_EXPRESSION evaluate a core expression  
- check error code  
- show result

