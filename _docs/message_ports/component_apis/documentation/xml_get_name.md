---
layout: commandcall
category: CommandCall
title: "XML_GET_NAME"
tags: 1.3 1.5
---

XML_GET_NAME returns the name of an element.

# Syntax:  

```adoscript
{% raw %}
CC "Documentation" XML_GET_NAME	[ node:intValue ]

#--> RESULT name:strValue ecode:intValue .

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`node`|intValue, ID of another node than the current for which to get the name.|
|`index`|intValue, get the n-th child: 0 for the first child, 1 for the 2nd...|

# Returns:  

ecode - intValue, Contains the error code or is 0 in case of success; 3 - XML_NOPARSER - a file has to be opened first; 15 - XML_NODENOTEXISTING - the element with the specified id is not existing are already discarded from memory;
|`name`|strValue, name of the node|

# Remarks:



# See Also:  



Example 1:

```adoscript
{% raw %}

# parse the xml string: <MAIN><SUB/></MAIN>
PROCEDURE PARSESUB {
   CC "Documentation" XML_GETPARENT
   CC "Documentation" XML_GETNAME node:(parent)
   # will return "MAIN"
}

{% endraw %}
```
{: .line-numbers}

