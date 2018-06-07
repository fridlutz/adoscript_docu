---
layout: commandcall
category: CommandCall
title: "XML_FIND_NODE"
tags: 1.3 1.5
---

XML_FIND_NODE finds a node that has previously been held in memory with XML_HOLD.

# Syntax:  

```adoscript
{% raw %}
CC "Documentation" XML_FIND_NODE	[ nodename:strValue] [ holdid:intValue]
									[ attribute:strValue] [ index:intValue]

#--> RESULT ecode:intValue nodeid:intValue .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`holdid`|integer, a positive Integer identifying the holded nodes (used for XML_RELEASE).|
|`nodename`|strValue, the name of a node|
|`attribute`|strValue, an attribute and its value separated by '='|
|`index`|intValue, find the n-th node matching the search creteria. Starting index is 0 (default).|


# Returns:  

ecode - intValue, Contains the error code or is 0 in case of success; 3 - XML_NOPARSER - a file has to be opened first; 8 - XML_MISSINGATTRIBUTE - no name, holdid and attribute has been specified; 18 - XML_INVALIDATTRIBUTESEARCH - the search for an attribute has not been specified in the correct syntax; 19	- XML_NODENOTFOUND - the node has not been found. It is either not existing or has not yet been parsed or has not been held in memory.
|`nodeid`|intValue, the id of the node returned|

# Remarks:

Called within a callback procedure.

Nodes can be searched by name, hold ID, attribute value or a combination of these three.

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
   # returns the id for the BROTHER node. Without a call to XML_HOLD in the
   # brother node, the BROTHER node would already be discarded from memory
   # again as only direct parent nodes of the currently parsed node are held
   # in memory on default.
}

{% endraw %}
```
{: .line-numbers}

