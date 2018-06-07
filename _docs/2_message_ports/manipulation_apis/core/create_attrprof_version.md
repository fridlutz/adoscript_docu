---
layout: commandcall
category: CommandCall
title: "CREATE_ATTRPROF_VERSION"
tags: 1.3 1.5
---

CREATE_ATTRPROF_VERSION creates a new AttrProf version of the given AttrProf thread passed in apthreadid.

# Syntax:  

```adoscript
{% raw %}
CC "Core" CREATE_ATTRPROF_VERSION apthreadid:intValue apversionstr:strValue


# --> RESULT ecode:intValue apversionid:intValue .

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`apthreadid`|intValue|
|`apversionstr`|strValue|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`apversionid`|intValue|

# Remarks:

The new version is passed in apversionstr.  
The version string is a number in the format "YYYYMMDD" (Y:Year, M:Month,D:Day). If one or more of these is not defined in the library attributes of the  
GP-Library it has to be set to zero. For example:  
VERSIONING  
MONTH_FIELD  
TEXT_FIELD "."  
DAY_FIELD  
would mean a version string for "1. April" would be "00000401".

IMPORTANT: This command can only be used in a versionized application library!

# See Also:  



Example 1:

```adoscript
{% raw %}

# determine all directories of the root group
CC "Core" GET_ALL_ATTRPROF_SUBDIRS
SET apdirid:(VAL token (apdirids, 0, " "))

# get all threads in the first group
CC "Core" GET_ALL_ATTRPROF_THREADS_IN_DIR apdirid:(apdirid)
SET apthreadid:(VAL token (apthreadids, 0, " "))

# determine the class of the first AttrProf in the first group
CC "Core" GET_ATTRPROF_CLASS_OF_THREAD apthreadid:(apthreadid)
SET apclassid:(apclassid)

# now we're ready to create a new AttrProfVersion
CC "Core" debug CREATE_ATTRPROF_VERSION_EXT apclassid:(apclassid) apdirid:(apdirid) apthreadname:"Foo" apversionstr:"00000405"

# get thread id and store it
CC "Core" GET_ATTRPROF_THREAD_OF_VERSION apversionid:(apversionid)
SET mythread:(apthreadid)

# create another version
CC "Core" debug CREATE_ATTRPROF_VERSION apthreadid:(apthreadid) apversionstr:"00000706"

# keep version id in mind
SET myversion:(apversionid)

# create a third version
CC "Core" debug CREATE_ATTRPROF_VERSION apthreadid:(apthreadid) apversionstr:"00000806"

# rename thread (-> and all versions!)
CC "Core" debug RENAME_ATTRPROF_THREAD apthreadid:(apthreadid) apthreadname:("Renamed Foo2!")

# delete version which we kept in mind
CC "Core" debug DELETE_ATTRPROF_VERSION apversionid:(myversion)

# delete whole thread
CC "Core" debug DELETE_ATTRPROF_THREAD apthreadid:(mythread)

{% endraw %}
```
{: .line-numbers}
Preparing:  
- Get all root dirs  
- Get all AttrProfs of first root dir  
- Get class of first AttrProf in first root dir

Interesting:  
- Create new thread -&gt; Returns version id  
- Get thread id from version id and store it  
- Create seconde version and store version id  
- Create third version  
- Rename complete thread (with all versions)  
- Delete second version  
- Delete complete thread  
