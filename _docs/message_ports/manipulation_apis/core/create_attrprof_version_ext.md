---
layout: commandcall
category: CommandCall
title: "CREATE_ATTRPROF_VERSION_EXT"
tags: 1.3 1.5
---

CREATE_ATTRPROF_VERSION_EXT creates a completely new AttrProf version from the given class (apclassid) in the given directory (apdirid).

# Syntax:  

```adoscript
{% raw %}
CC "Core" CREATE_ATTRPROF_VERSION_EXT apclassid:intValue apdirid:intValue apthreadname:strValue apversionstr:strValue


# --> RESULT ecode:intValue apversionid:intValue .

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`apclassid`|intValue|
|`apdirid`|intValue|
|`apthreadname`|strValue|
|`apversionstr`|strValue|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`apversionid`|intValue|

# Remarks:


The name is specified via apthreadname and the version can be passed via apversionstr.  
The version string is a number in the format "YYYYMMDD" (Y:Year, M:Month,D:Day). If one or more of these is not defined in the library attributes of the  
GP-Library it has to be set to zero. For example:  
VERSIONING  
MONTH_FIELD  
TEXT_FIELD "."  
DAY_FIELD  
would mean a version string for "1. April" would be "00000401".

IMPORTANT: if versioning is NOT enabled, you have to pass an empty string ("") to apversionstr!

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
CC "Core" debug CREATE_ATTRPROF_VERSION_EXT apclassid:(apclassid) apdirid:(apdirid) apthreadname:"Foo" apversionstr:""

{% endraw %}
```
{: .line-numbers}

