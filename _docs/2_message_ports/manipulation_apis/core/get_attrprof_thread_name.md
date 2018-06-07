---
layout: commandcall
category: CommandCall
title: "GET_ATTRPROF_THREAD_NAME"
tags: 1.3 1.5
---

GET_ATTRPROF_THREAD_NAME returns the name of an attribute profile thread.

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_ATTRPROF_THREAD_NAME apthreadid:id .


#-->RESULT ecode:intValue apthreadname:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`apthreadid`|id, the specified attribute profile thread is passed in the apthreadid parameter.|

# Returns:  

|`ecode`|intValue, the return variable ecode is set to zero if command succeeded and to a non zero value if failed.|
|`apthreadname`|strValue, the return variable apthreadname is set to the name of the attribute profile thread.|

# Remarks:



# See Also:  



Example 1:

```adoscript
{% raw %}

# get root directories
CC "Core" GET_ALL_ATTRPROF_SUBDIRS

# get all attribute profile threads in first root directory
CC "Core" GET_ALL_ATTRPROF_THREADS_IN_DIR apdirid:(VAL token(apdirids,0," "))
IF (ecode!=0)
{
  CC "AdoScript" ERRORBOX ("Error in GET_ALL_ATTRPPROF_THREADS_IN_DIR!")
  EXIT
}

# check if any attribute profiles were found
IF (LEN(apthreadids)=0)
{
  CC "AdoScript" ERRORBOX ("No attribute profiles found in root directory!")
  EXIT
}

# get name of first attribute profile found in first root directory
CC "Core" GET_ATTRPROF_THREAD_NAME apthreadid:(VAL token(apthreadids,0," "))
IF (ecode!=0)
{
  CC "AdoScript" ERRORBOX ("Error in GET_ATTRPROF_THREAD_NAME!")
  EXIT
}

# show this name
CC "AdoScript" INFOBOX ("First attribute profile in root directory is:\n"+apthreadname)

{% endraw %}
```
{: .line-numbers}

