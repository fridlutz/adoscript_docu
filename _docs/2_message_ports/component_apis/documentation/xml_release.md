---
layout: commandcall
category: CommandCall
title: "XML_RELEASE"
tags: 1.3 1.5
---

XML_RELEASE releases held nodes in memory.

# Syntax:  

```adoscript
{% raw %}
CC "Documentation" XML_RELEASE intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`<main_parameter>`|intValue, a positive integer value identifying the held nodes.|

# Returns:  

ecode - intValue, Contains the error code or is 0 in case of success; 3 - XML_NOPARSER - a file has to be opened first; 15 - XML_NODENOTEXISTING - the element with the specified id is not existing are already discarded from memory;

# Remarks:

Called within a callback procedure..

# See Also:  



Example 1:

```adoscript
{% raw %}

#
# parse the xml string: <MAIN><BROTHER name="Sepp"/><SISTER/><SUB/></MAIN>
#

# called for the BROTHER element
PROCEDURE REMEMBERNODE {
   CC "Documentation" XML_HOLD 2
}

# called for the SISTER element
PROCEDURE SEARCHANODE {
   CC "Documentation" XML_FIND holdid:2 attribute="name=Sepp"
   # returns the id for the BROTHER node.
   CC "Documentation" XML_RELEASE 2
   CC "Documentation" XML_FIND holdid:2 attribute="name=Sepp"
   # returns XML_NODENOTFOUND
}

{% endraw %}
```
{: .line-numbers}

