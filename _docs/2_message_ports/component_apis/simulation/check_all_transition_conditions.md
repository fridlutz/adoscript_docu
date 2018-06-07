---
layout: commandcall
category: CommandCall
title: "CHECK_ALL_TRANSITION_CONDITIONS"
tags: 1.3 1.5
---

This command checks the syntax of all transition conditions contained in a model. The model has to be specified by its modelid. If a transition condition defines or references a macro the macro definition is checked too.

# Syntax:  

```adoscript
{% raw %}
CC "Simulation" CHECK_ALL_TRANSITION_CONDITIONS modelid:intValue

#--> RESULT ecode:intValue 
			errtext:strValue 
			text:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|intValue|

# Returns:  

|`ecode`|intValue, 0 if the check was completed successfully or 1 if an error has ocurred|
|`errtext`|strValue,  INVALID_MODELID if the modelid given was not valid, NO_SUCCESSOR_RELATIONS_IN_MODEL if the model specified did not contain any relations of class successor or OK for no error|
|`text`|strValue, contains a line in the format **RelationID CheckResult\n** for every transition condition.|

# Remarks:

Possible CheckResults are  
*EXPECTED_PARENTHESIS
*EXPECTED_LOGICAL_OPERATOR
*ILLEGAL_OPERATOR
*ILLEGAL_TERM
*INCOMPLETE_COMPARISON
*INCOMPLETE_CONDITION
*NO_ERROR
*TRANS_PROBABILITY
*TREE_ALREADY_EXISTS
*TREE_CONSISTS_OF_TRUE
*UNKNOWN_OPERATOR

In case of a macro definition the CheckResult is preceded by "MACRO_DEFINITION-&gt;"  
In case of a macro reference the CheckResult is preceded by "REFERENCING_MACRO-&gt;"

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Core" GET_MODEL_ID modelname:"GP1" modeltype:"Gesch�ftsproze�modell"
CC "Simulation" CHECK_ALL_TRANSITION_CONDITIONS modelid:(modelid)
IF (ecode = 0)
{
  CC "AdoScript" INFOBOX (text)
}
ELSE
{
  CC "AdoScript" ERRORBOX (errtext)
}

{% endraw %}
```
{: .line-numbers}

![](/images/CHECK_ALL_TRANSITION_CONDITIONS.png)
