---
layout: commandcall
category: CommandCall
title: "SET_CWD"
tags: 1.3 1.5
---

SET_CWD sets the current working directory

# Syntax:  

```adoscript
{% raw %}
CC "AdoScript" SET_CWD path:strValue

# -->RESULT ecode:intValue .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`path`|strValue, the path to be set as current working directory|

# Returns:  

|`ecode`|intValue, has the value 0 if no errors occured, a value different than 0 if an error occured.|

# Remarks:

A relative path relates to the previous working directory.

# See Also:  

[GET_CWD](get_cwd.html "GET_CWD")  


Example 1:

```adoscript
{% raw %}

CC "AdoScript" GET_CWD
SET oldCwd:(cwd)
CC "AdoScript" SET_CWD path:("c:\\temp")
CC "AdoScript" GET_CWD
CC "AdoScript" INFOBOX ("The old CWD is: '" + oldCwd + "'.\n" +
                        "The new CWD is: '" + cwd + "'.")

{% endraw %}
```
{: .line-numbers}
Sets a new cwd and displays the old and current working directory it in an infobox.  
