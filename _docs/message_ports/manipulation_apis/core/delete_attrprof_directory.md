---
layout: commandcall
category: CommandCall
title: "DELETE_ATTRPROF_DIRECTORY"
tags: 1.3 1.5
---

DELETE_ATTRPROF_DIRECTORY deletes an existing attribute profil directory.

# Syntax:  

```adoscript
{% raw %}
CC "Core" DELETE_ATTRPROF_DIRECTORY apdirid:intValue

# --> RESULT ecode:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`apdirid`|intValue, the directory is specified by its id|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|

# Remarks:

The whole substructure of this directory will be deleted. All attribute profiles in this directory or in a subdirectory will be deleted as well.

# See Also:  



Example 1:

```adoscript
{% raw %}

# create an attribute profile directory
CC "Core" CREATE_ATTRPROF_DIRECTORY apdirname:"New AttrProfDir"
IF (ecode!=0)
{
  CC "AdoScript" INFOBOX ("Error in CREATE_ATTRPROF_DIRECTORY!")
  EXIT
}

# get directory name of directory id
CC "Core" GET_ATTRPROF_DIRECTORY_NAME apdirid:(apdirid)
IF (ecode!=0)
{
  CC "AdoScript" ERRORBOX ("Error in GET_ATTRPROF_DIRECTORY_NAME!")
  EXIT
}

CC "AdoScript" INFOBOX ("Added: \""+(apdirname)+"\" ID: "+(STR apdirid))

# rename directory
CC "Core" RENAME_ATTRPROF_DIRECTORY apdirid:(apdirid) apdirname:("Renamed AttrProfDir")
IF (ecode!=0)
{
  CC "AdoScript" INFOBOX ("Error in RENAME_ATTROPROF_DIRECTORY!")
  EXIT
}

# get new directory name
CC "Core" GET_ATTRPROF_DIRECTORY_NAME apdirid:(apdirid)
IF (ecode!=0)
{
  CC "AdoScript" ERRORBOX ("ERROR GET_ATTRPROF_DIRECTORY_NAME #2!")
  EXIT
}

CC "AdoScript" INFOBOX ("Renamed to \""+(apdirname)+"\"!")

# delete directory name
CC "Core" DELETE_ATTRPROF_DIRECTORY apdirid:(apdirid)
IF (ecode!=0)
{
  CC "AdoScript" ERRORBOX ("Error in DELETE_ATTRPROF_DIRECTORY!")
  EXIT
}
CC "AdoScript" INFOBOX ("Deleted \""+(apdirname)+"\" successfully!")

{% endraw %}
```
{: .line-numbers}

