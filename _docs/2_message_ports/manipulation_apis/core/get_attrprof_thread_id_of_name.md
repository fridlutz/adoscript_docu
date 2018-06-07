---
layout: commandcall
category: CommandCall
title: "GET_ATTRPROF_THREAD_ID_OF_NAME"
tags: 1.3 1.5
---

GET_ATTRPROF_THREAD_ID_OF_NAME returns the ID of the AttrProf with the given name of the given AttrProf-class.

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_ATTRPROF_THREAD_ID_OF_NAME apthreadname:str apclassname:str .


#-->RESULT ecode:intValue apthreadid:id
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`apthreadname`|str|
|`apclassname`|str|

# Returns:  

|`ecode`|intValue, the return variable ecode is set to zero if command succeeded and to a non zero value if failed.|
|`apthreadid`|id, the return variable apthreadid contains the ID of the AttrProf thread which matches or -1 if an error occured.|

# Remarks:



# See Also:  



Example 1:

```adoscript
{% raw %}

# Assume there is a AP thread "ganztags" of AP class "Anwesenheit" (Standard-AB)
CC "Core" GET_ATTRPROF_THREAD_ID_OF_NAME apthreadname:"ganztags" apclassname:"Anwesenheit"

# show this name
CC "AdoScript" INFOBOX ("The ID is: " + STR (apthreadid))

{% endraw %}
```
{: .line-numbers}

