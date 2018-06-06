---
layout: commandcall
category: CommandCall
title: "GET_PATH"
tags: 1.3 1.5
---



# Syntax:  

```adoscript
{% raw %}
CC "Application" GET_PATH [ strValue ] [ path-only [ append-delimiter ] ]

#--> RESULT path:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`<main_parameter>`|strValue, when specified, it contains a file and GET_PATH returns the absolute path to this file. When no filename is specified, the installation directory of ADOxx is returned.|
|`path-only`|modifier, when specified, the filename is omitted.|
|`append-delimiter`|modifier, when specified, the '\' is appended at the end of the path.|

# Returns:  

|`path `|strValue, contains the absolute path to the file.|

# Remarks:

If GET_PATH is called on a root path (when giving no filename having e.g. the ADOxx directory being mapped to a network drive),  
the path will have an appended \ character anyway.

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Application" debug GET_PATH
CC "Application" debug GET_PATH "Aadma.exe"
CC "Application" debug GET_PATH "Aadma.exe" path-only
CC "Application" debug GET_PATH "Aadma.exe" path-only append-delimiter

{% endraw %}
```
{: .line-numbers}

The third statement produces the following message box  
![](/images/GET_PATH.png)
