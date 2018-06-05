---
layout: commandcall
category: CommandCall
title: "GET_ALL_ATTRPROF_THREADS_IN_DIR"
tags: 1.3 1.5
---

The command GET_ALL_ATTRPROF_THREADS_IN_DIR returns all attribute profile threads in the specified directory.

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_ALL_ATTRPROF_THREADS_IN_DIR apdirid:id .


#-->RESULT ecode:intValue apthreadids:ids
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`apdirid`|id, the attribute profile directory is passed in the attribute apdirid.|

# Returns:  

|`ecode`|intValue, the return value ecode is zero if command was executed sucessfully and non zero on failure.|
|`apthreadids`|ids, the return value apthreadids lists the ids of all attribute profile threads found in specified directory.|

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

CC "AdoScript" INFOBOX ("Folloing attribute profile threads were found in the root directory:\n"+apthreadids)

{% endraw %}
```
{: .line-numbers}

