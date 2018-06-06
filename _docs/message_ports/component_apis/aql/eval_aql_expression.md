---
layout: commandcall
category: CommandCall
title: "EVAL_AQL_EXPRESSION"
tags: 1.3 1.5
---

EVAL_AQL_EXPRESSION will evaluate an AQL string.

# Syntax:  

```adoscript
{% raw %}
CC "AdoScript" EVAL_AQL_EXPRESSION expr: strValue ( modelid: intValue | modelscope ) .

# --> RESULT ecode: intValue objids: strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`expr`|strValue, specifies the AQL string to be evaluated|
|`modelid`|intValue, specifies the scope of the query|
|`modelscope`|modifier, if passed, the scope of the query will be all models and the result will be all models fulfilling the AQL expression; this corresponds to "Search models by model attributes".|

# Returns:  

|`ecode`|intValue, is 0 if the evaluation yielded no error or the error code otherwise.|
|`objids`|strValue, contains the list of found objects or models separated by blanks|

# Remarks:

If the argument modelid is passed, the scope of the query will be this model and the result will be all objects and connectors fulfilling the AQL expression (this corresponds to doing a userdefined query with the chosen model).

If the argument modelscope is passed, the scope of the query will be all models and the result will be all models fulfilling the AQL expression (this corresponds to "Search models by model attributes").

# See Also:  

[CHECK_AQL_EXPRESSION](check_aql_expression.html "CHECK_AQL_EXPRESSION")  


Example 1 (Get all objects of class "A" in a certain model):

```adoscript
{% raw %}
CC "AQL" EVAL_AQL_EXPRESSION expr:"<\"A\">" modelid: (modelid)
IF (ecode = 0) {
    CC "AdoScript" INFOBOX ("Found objects: " + objids)
}
ELSE {
    CC "AdoScript" INFOBOX "An error has occured!"
}
{% endraw %}
```
{: .line-numbers}


Example 2 (Get all models of modeltype "Sample Target Model"):

```adoscript
{% raw %}
CC "AQL" EVAL_AQL_EXPRESSION expr: "<\"Sample Target Model\">" modelscope
IF (ecode = 0) {
    CC "AdoScript" INFOBOX ("Found models: " + objids)
}
ELSE {
    CC "AdoScript" INFOBOX "An error has occured!"
}
{% endraw %}
```
{: .line-numbers}

