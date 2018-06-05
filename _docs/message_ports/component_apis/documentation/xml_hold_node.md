---
layout: commandcall
category: CommandCall
title: "XML_HOLD_NODE"
tags: 1.3 1.5
---

XML_HOLD_NODE keeps the node in memory until it is explicitly released.

# Syntax:  

```adoscript
{% raw %}
CC "Documentation" XML_HOLD_NODE intVal node:intValue

#--> RESULT ecode:intValue 
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`<main_parameter>`|intVal, a positive integer value identifying the held nodes. Multiple nodes can be held under one holdID. The ID is used when nodes should be released again. XML_HOLD_NODE can only be called once per XML node.|
|`node`|intVal, ID of a parent node of the current node that should be held.|

# Returns:  

ecode - intValue, Contains the error code or is 0 in case of success; 3 - XML_NOPARSER - a file has to be opened first; 15 - XML_NODENOTEXISTING - the node with the specified id is not existing are already discarded from memory; 17 - XML_NODEALREADYHELD - XML_HOLD_NODE has already been called for the specified node.

# Remarks:

Called within a callback procedure.

Usually only parent nodes can be queried in callback-procedures because only the parent nodes up to the rootnode are kept in memory. Call this method to hold the node in memory until you release it again with XML_RELEASE.

# See Also:  



Example 1:

```adoscript
{% raw %}

# parse the xml string: <MAIN><BROTHER name="Sepp"/><SISTER/><SUB/></MAIN>

# called for the BROTHER element
PROCEDURE REMEMBERNODE {
    CC "Documentation" XML_HOLD 2
}

# called for the SISTER element
PROCEDURE SEARCHANODE {
    CC "Documentation" XML_FIND holdid:2 attribute="name=Sepp"
    # returns the id for the BROTHER node. Without a call to XML_HOLD_NODE in the
    # brother node, the BROTHER node would already be discarded from memory
    # again as only direct parent nodes of the currently parsed node are held
    # in memory on default.
}

{% endraw %}
```
{: .line-numbers}

