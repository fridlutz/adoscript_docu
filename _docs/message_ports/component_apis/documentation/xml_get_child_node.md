---
layout: commandcall
category: CommandCall
title: "XML_GET_CHILD_NODE"
tags: 1.3 1.5
---

XML_GET_CHILD_NODE returns the ID of a child node.

# Syntax:  

```adoscript
{% raw %}
CC "Documentation" XML_GET_CHILD_NODE [ node:intValue ] [ index:intValue ]

#--> RESULT ecode:intValue child:intValue 
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`node`|intValue, ID of another node than the current for which to get an attribute.|
|`index`|intValue, get the n-th child: 0 for the first child, 1 for the 2nd...|

# Returns:  

ecode - intValue, Contains the error code or is 0 in case of success; 3 - XML_NOPARSER - a file has to be opened first; 15 - XML_NODENOTEXISTING - the element with the specified id is not existing are already discarded from memory; 16 - XML_NODEHASNOCHILDREN - you tried to a child that does not exist.
|`child`|intValue, the ID of the node|

# Remarks:

Called within a callback procedure.

Only childnodes that have already been parsed and that are held in memory with XML_HOLD will be retured! If in the example below, the procedure PARSESUB was invoked in the start node, no child nodes would be returned because none would have been parsed yet.

# See Also:  



Example 1:

```adoscript
{% raw %}

# parse the xml string: <MAIN><BROTHER><SISTER><SUB/></MAIN>
PROCEDURE PARSESUB {
   CC "Documentation" XML_GET_PARENT_NODE
   CC "Documentation" XML_GET_CHILD_NODE node:(parent) index:1
   # returns id for the SISTER-element
   CC "Documentation" XML_GET_CHILD_NODE node:(parent) index:2
   # returns id for the SUB-element
   CC "Documentation" XML_GET_CHILD_NODE node:(parent) index:22
   # returns XML_NODEHASNOCHILDREN
}

CC "Documentation" XML_ADD_CALLBACK "PARSESUB" name:"MAIN" type:"elementend"

{% endraw %}
```
{: .line-numbers}

