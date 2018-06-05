---
layout: commandcall
category: CommandCall
title: "GET_ALL_ATTRPROF_VERSIONS_OF_THREAD"
tags: 1.3 1.5
---

The command GET_ALL_ATTRPROF_VERSIONS_OF_THREAD returns a list of all attribute profile versions of specified attribute profile thread.

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_ALL_ATTRPROF_VERSIONS_OF_THREAD apthreadid:id


#-->RESULT ecode:intValue apversionids:ids
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`apthreadid`|id, the specified attribute profile thread is passed as core id in the parameter apthreadid.|

# Returns:  

|`ecode`|intValue, the return value ecode is zero if command was executed sucessfully and non zero on failure.|
|`apversionids`|ids, the return value apversionids contains a list with ids of all attribute profile versions.|

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

CC "AdoScript" INFOBOX ("Verions of first attribute profile:\n"+apversionids)

{% endraw %}
```
{: .line-numbers}

