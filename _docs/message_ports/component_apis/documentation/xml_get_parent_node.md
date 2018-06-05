---
layout: commandcall
category: CommandCall
title: "XML_GET_PARENT_NODE"
tags: 1.3 1.5
---

XML_GET_PARENT_NODE returns the ID of the parent node.

# Syntax:  

```adoscript
{% raw %}
CC "Documentation" XML_GET_PARENT_NODE	node:intValue [ level:intValue ]

#--> RESULT ecode:intValue parent:intValue .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`node`|intValue, ID of another node than the current for which to get an attribute.|
|`level`|intValue, get the n-th parent: 1 for the direct parent, 2 for the parent of the parent, etc.; default is 1.|

# Returns:  

ecode - intValue, Contains the error code or is 0 in case of success; 3 - XML_NOPARSER - a file has to be opened first; 15 - XML_NODENOTEXISTING - the element with the specified id is not existing are already discarded from memory; 20 - XML_NODEHASNOPARENT - you tried to get the parent of the root node.

# Remarks:

Called within a callback procedure.

The ID of the parent node is returned via parent.

# See Also:  



Example 1:

```adoscript
{% raw %}

# parse the xml string: <MAIN><SUB/></MAIN>
PROCEDURE PARSESUB {
    CC "Documentation" XML_GET_PARENT_NODE
    # returns id for <MAIN>
}

{% endraw %}
```
{: .line-numbers}

