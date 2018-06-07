---
layout: commandcall
category: CommandCall
title: "GET_ATTRPROF_CLASS_OF_VERSION"
tags: 1.3 1.5
---

GET_ATTRPROF_CLASS_OF_VERSION determines the AttrProf class which is referenced by the give attribute profile version.

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_ATTRPROF_CLASS_OF_VERSION apversionid:intValue . 


#-->RESULT ecode:intValue apclassid:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`apversionid`|intValue, the attribute profile version is passed as its id in the parameter apversionid.|

# Returns:  

|`ecode`|intValue, the return value ecode is set to zero if function succeeded and to a non zero value else.|
|`apclassid`|intValue, the ID of the referenced AttrProf class is returned in apclassid.|

# Remarks:



# See Also:  



Example 1:

```adoscript
{% raw %}

# get root directory id
CC "Core" GET_ALL_ATTRPROF_SUBDIRS

# get all attribute profile threads in this directory
CC "Core" GET_ALL_ATTRPROF_THREADS_IN_DIR apdirid:(VAL token(apdirids,0," "))

# pick the first thread
SET mythread:(token(apthreadids,0," "))
# get its class
CC "Core" GET_ATTRPROF_CLASS_OF_THREAD apthreadid:(VAL mythread)

# show this class id
CC "AdoScript" INFOBOX ("ClassID: "+(STR apclassid))

# get all versions of first thread
CC "Core" GET_ALL_ATTRPROF_VERSIONS_OF_THREAD apthreadid:(VAL mythread)

# pick first verison
SET myversion:(token(apversionids,0," "))
# get its class id
CC "Core" GET_ATTRPROF_CLASS_OF_VERSION apversionid:(VAL myversion)

# show this class id
CC "AdoScript" INFOBOX ("ClassID: "+(STR apclassid))

{% endraw %}
```
{: .line-numbers}

