---
layout: commandcall
category: CommandCall
title: "GET_ALL_ATTRPROF_SUBDIRS"
tags: 1.3 1.5
---

GET_ALL_ATTRPROF_SUBDIRS returns a list of all subdirectory ids of directory apdirid.

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_ALL_ATTRPROF_SUBDIRS [apdirid:id] .


#-->RESULT ecode:intValue apdirids:ids
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`apdirid`|id, the optional parametere apdirid specifies the parent directory.|

# Returns:  

|`ecode`|intValue, the result ecode is set to zero if function succeeded and to a non zero value if failed.|
|`apdirids`|ids, the result apdirids holds a list of all subdirectory ids.|

# Remarks:




If no parent directory is specified GET_ALL_ATTRPROF_SUBDIRS returns all super directories.





# See Also:  



Example 1:

```adoscript
{% raw %}

# get all subdirs of root directory
CC "Core" GET_ALL_ATTRPROF_SUBDIRS
IF (ecode!=0)
{
  CC "AdoScript" ERRORBOX ("Error in GET_ALL_ATTRPROF_SUBDIRS")
  EXIT
}

# get all directory names
SET items:("")
FOR id in:(apdirids)
{
  CC "Core" GET_ATTRPROF_DIRECTORY_NAME apdirid:(VAL id)
  IF (ecode!=0)
  {
    CC "AdoScript" ERRORBOX ("Error in GET_ATTRPROF_DIRECTORY_NAME!")
    EXIT
  }
  SET items:(items+(apdirname)+"@")
}

# check if any directories found
IF (LEN(apdirname)=0)
{
  CC "AdoScript" ERRORBOX ("No apdirnames!")
  EXIT
}

# delete last token
SET items:(copy(items,0,LEN(items)-1))

# show all entries
CC "AdoScript" LISTBOX title:"AttrProfSubDirs" entries:(items) toksep:"@" oktext:"OK" boxtext:"SubDirs found:"

{% endraw %}
```
{: .line-numbers}

