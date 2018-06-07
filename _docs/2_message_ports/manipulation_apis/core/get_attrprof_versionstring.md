---
layout: commandcall
category: CommandCall
title: "GET_ATTRPROF_VERSIONSTRING"
tags: 1.3 1.5
---

GET_ATTRPROF_VERSIONSTRING returns the string value of the version of specified attribute profile version.

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_ATTRPROF_VERSIONSTRING apversionid:id .


#-->RESULT ecode:intValue apversionstr:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`apversionid`|id, the specified attribute profile version is passed in the apversionid parameter.|

# Returns:  

|`ecode`|intValue, the return variable ecode is set to zero if command succeeded and to a non zero value if failed.|
|`apversionstr`|strValue, the return variable apversionstr is set to the version string of the attribute profile version.|

# Remarks:

Important: This works only in applibs where versioning is enabled. If the applib has no versioning enabled, the return value is always an empty string and ecode:0

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


# loop for all verions
FOR id in:(apversionids)
{
 
# get version string of attribute profile version id
  CC "Core" GET_ATTRPROF_VERSIONSTRING apversionid:(VAL id)
  IF (ecode!=0)
  {
    CC "AdoScript" ERRORBOX ("Error in GET_ATTROPROF_VERSIONSTRING!")
    EXIT
  }
  CC "AdoScript" INFOBOX ("Version number: "+apversionstr)
}

{% endraw %}
```
{: .line-numbers}

