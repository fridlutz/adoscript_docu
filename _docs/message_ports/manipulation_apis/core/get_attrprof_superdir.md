---
layout: commandcall
category: CommandCall
title: "GET_ATTRPROF_SUPERDIR"
tags: 1.3 1.5
---

GET_ATTRPROF_SUPERDIR returns the name of the attribute profile super directory, of which the passed attribute profile directory is a subdirectory.

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_ATTRPROF_SUPERDIR apdirid:id .


#-->RESULT ecode:intValue superapdirid:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`apdirid`|id, the directory is specified by its id passed in apdirid.|

# Returns:  

|`ecode`|intValue, the result ecode is set to zero if function succeeded and to a non zero value if failed.|
|`superapdirid`|intValue, the result superapdirid holds the core id of the super directory.|

# Remarks:



# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Core" GET_ALL_ATTRPROF_SUBDIRS apdirid:(0)
IF (LEN(apdirids)=0)
{
  CC "AdoScript" ERRORBOX ("Error in GET_ALL_ATTRPROF_SUBDIRS!\nNo read permission or no attrprof dirs definied?")
  EXIT
}
SET rootdirid:(VAL token(apdirids,0," "))
CC "Core" GET_ATTRPROF_DIRECTORY_NAME apdirid:(rootdirid)
SET rootname:(apdirname)
CC "AdoScript" INFOBOX ("First root directory is:\n\""+rootname+"\"")

CC "Core" GET_ALL_ATTRPROF_SUBDIRS apdirid:(rootdirid)
IF (LEN(apdirids)=0)
{
  CC "AdoScript" ERRORBOX ("Error in GET_ALL_ATTRPROF_SUBDIRS!\nNo read permission or no subdirs defined?")
  EXIT
}
SET subdirid:(VAL token(apdirids,0," "))
CC "Core" GET_ATTRPROF_DIRECTORY_NAME apdirid:(subdirid)
SET subname:(apdirname)
CC "AdoScript" INFOBOX ("First subdir of \""+rootname+"\" is:\n\""+subname+"\"")

CC "Core" GET_ATTRPROF_SUPERDIR apdirid:(subdirid)
IF (ecode!=0)
{
  CC "AdoScript" ERRORBOX ("Error in GET_ATTRPROF_SUPERDIR!")
  EXIT
}
CC "Core" GET_ATTRPROF_DIRECTORY_NAME apdirid:(superapdirid)
CC "AdoScript" INFOBOX ("Returned superdir from \""+subname+"\" is:\n\""+apdirname+"\"")

{% endraw %}
```
{: .line-numbers}
- Get all root directories  
- Check if there are any (LEN(apdirids)=0)?  
- Get name of first root dir and show it  
- Get all subdirs from first root dir  
- Check if there are any  
- Get name of first subdir and show it  
- Get SUPERDIR of first subdir (must be the first root dir!)  
- Check for error  
- Get name of superdir and show it

# Remarks:  
To successfully run this example you should at least have defined one root directory and one subdirectory in the attribute profile setting dialog.  
