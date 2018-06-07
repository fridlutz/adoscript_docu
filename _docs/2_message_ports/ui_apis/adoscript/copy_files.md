---
layout: commandcall
category: CommandCall
title: "COPY_FILES"
tags: 1.3 1.5
---

COPY_FILES copies multiple files and/or directories to another directory.

# Syntax:

```adoscript
{% raw %}
CC "AdoScript" COPY_FILES strValue to:strValue [ no-overwrite ]

# --> RESULT ecode:intValue .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`<main-parameter>`|strValue, string specifying a list of files that shall be copied. This can be the name of one file, e.g. "d:\\temp\\test.html", or a name containing wildcards, e.g. "d:\\temp\\**.html".|
|`to`|strValue, the name of the target directory|
|`no-overwrite`|modifier, if specified, copied files must not overwrite files with same name in the target directory. Then, if there is a file to copy which already exists in the target directory, COPY_FILES fails. Without no-overwrite, if there is a file to copy which already exists in the target directory, COPY_FILES overwrites the existing file and succeeds.|

# Returns:  

|`ecode`|intValue|

# Remarks:

The target directory must exist. Relative paths relate to the current working directory (CWD).

If a (directly specified or matching) source file name is the name of a directory, a complete (recursive) copy of that directory is created in the target directory.

This command works only with files in the file system, not with files in the database. FILE_COPY works with database files, but does not interpret wildcards..

# See Also:  

[FILE_COPY](file_copy.html "FILE_COPY")  


Example 1:

```adoscript
{% raw %}

CC "AdoScript" COPY_FILES "d:\\temp1\\**.html" to:"d:\\temp2" overwrite-existing

{% endraw %}
```
{: .line-numbers}

