---
layout: commandcall
category: CommandCall
title: "MOVE_FILES"
tags: 1.3 1.5
---

MOVE_FILES moves multiple files and/or directories to another directory.

# Syntax:  

```adoscript
{% raw %}
CC "AdoScript" MOVE_FILES strValue to:strValue

# --> RESULT ecode:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`<main-parameter>`|strValue, specifies the files which shall be moved|
|`to`|strValue, the name of the target directory where the files shall be moved to. This can be the name of one file, e.g. "d:\\temp\\test.html", or a name containing wildcards, e.g. "d:\\temp\\**.html". Relative paths relate to the current working directory (CWD).|

# Returns:  

|`ecode`|intValue|

# Remarks:

The target directory must exist.

If a (directly specified or matching) source file name is the name of a directory, a moving of the complete directory to the target directory is performed.

MOVE_FILES works only with files in the file system, not with files in the database.

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "AdoScript" MOVE_FILES "d:\\temp1\\**.html" to:"d:\\temp2"

{% endraw %}
```
{: .line-numbers}

