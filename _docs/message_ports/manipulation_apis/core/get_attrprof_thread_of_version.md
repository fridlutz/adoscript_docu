---
layout: commandcall
category: CommandCall
title: "GET_ATTRPROF_THREAD_OF_VERSION"
tags: 1.3 1.5
---

The command GET_ATTRPROF_THREAD_OF_VERSION returns the thread of the specified version of an attribute profile.

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_ATTRPROF_THREAD_OF_VERSION apversionid:id


#-->RESULT ecode:intValue apthreadid:ids
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`apversionid`|id, the attribute profile version is passed as core id in the parameter apversionid.|

# Returns:  

|`ecode`|intValue, the return value ecode is zero if command was executed sucessfully and non zero on failure.|
|`apthreadid`|ids, the return value apthreadid contains a list with all model versions.|

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

# get all versions of first thread of first root directory
CC "Core" GET_ALL_ATTRPROF_VERSIONS_OF_THREAD apthreadid:(VAL token(apthreadids,0," "))
IF (ecode!=0)
{
  CC "AdoScript" ERRORBOX ("Error in GET_ALL_ATTRPROF_VERSIONS_OF_THREAD!")
  EXIT
}

# back: get thread of version
CC "Core" GET_ATTRPROF_THREAD_OF_VERSION apversionid:(VAL token(apversionids,0," "))
IF (ecode!=0)
{
  CC "AdoScript" ERRORBOX ("Error in GET_ATTRPROF_THREAD_OF_VERSION!")
  EXIT
}
CC "AdoScript" INFOBOX ("Thread is: "+(STR apthreadid))

{% endraw %}
```
{: .line-numbers}

