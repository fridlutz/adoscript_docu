---
layout: commandcall
category: CommandCall
title: "GET_ALL_ATTRPROFS_IN_MODEL"
tags: 1.3 1.5
---

GET_ALL_ATTRPROFS_IN_MODEL determines all attribute profiles which are referenced from the model specified by modelid. For this function to succeed, the model must be at least loaded in the core (no write access required).

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_ALL_ATTRPROFS_IN_MODEL modelid:id .


#-->RESULT ecode:intValue apversions:string
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|id, the parameter modelid specifies the source model.|

# Returns:  

|`ecode`|intValue, the result ecode is set to zero if function succeeded and to a non zero value if failed.|
|`apversions`|string|

# Remarks:




The result apversions is itself a LEO string with the following layout (0-n times):

APREF srcobjid:id srcattrid:id apversionid:id

srcobjid is the ID of the source object  
srcattrid is the ID of the source attribute  
apversionid is the ID of the referenced AttrProf or -1 if it is a broken AttrProf reference.

# See Also:  



Example 1:

```adoscript
{% raw %}

SEND "GET_ACTIVE_MODEL" to:"Modeling" answer:modelid
CC "Core" debug GET_ALL_ATTRPROFS_IN_MODEL modelid:(VAL modelid)

{% endraw %}
```
{: .line-numbers}

