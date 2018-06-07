---
layout: commandcall
category: CommandCall
title: "DELETE_FILES"
tags: 1.3 1.5
---

DELETE_FILES deletes multiple files and/or directories.

# Syntax:  

```adoscript
{% raw %}
CC "AdoScript" DELETE_FILES strValue

#--> RESULT ecode:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`<main-parameter>`|strValue, specifies file(s)|

# Returns:  

|`ecode`|intValue, contains the error code or is 0 in case of success.|

# Remarks:

The files which shall be deleted are specified with the main parameter. This can be the name of one file, e.g. "d:\\temp\\test.html", or a name containing wildcards, e.g. "d:\\temp\\**.html". Relative paths relate to the current working directory (CWD).  
If a (directly specified or matching) source file name is the name of a directory, a complete (recursive) deletion of that directory is performed.

This command works only with files in the file system, not with files in the database. FILE_DELETE works with database files, but does not interpret wildcards.

# See Also:  

[FILE_DELETE](file_delete.html "FILE_DELETE")  


Example 1:

```adoscript
{% raw %}

CC "AdoScript" DELETE_FILES "d:\\temp1\\**.html"

{% endraw %}
```
{: .line-numbers}

