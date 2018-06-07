---
layout: commandcall
category: CommandCall
title: "XML_GET_ATTRIBUTE"
tags: 1.3 1.5
---

XML_GET_ATTRIBUTE returns an attribute value of the current node.

# Syntax:  

```adoscript
{% raw %}
CC "Documentation" XML_GET_ATTRIBUTE strValue [ node:intValue ]

#--> RESULT ecode:intValue value:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`<main_parameter>`|strValue, the name of the Attribute to get the value from.|
|`node`|intValue, ID of another node than the current for which to get an attribute. If no node is specified, the current node is queried.|

# Returns:  

ecode - intValue, Contains the error code or is 0 in case of success. 3 - XML_NOPARSER - a file has to be opened first; 8 - XML_MISSINGATTRIBUTE
No name, holdid and attribute has been specified; 15 - XML_NODENOTEXISTING - the element with the specified id is not existing are already discarded from memory; 16 - XML_ATTRIBUTENOTEXISTING - the specified attribute does not exist in the element.

# Remarks:

Called within a callback procedure.

Also attributes of other elements than the current can be queried. But they will only return values, when the element is currently held in memory. If, for example, an element that has not yet been parsed or an element that has already been parsed but discarded again is queried, an error code will be returned. By default, all elements that have no child elements are discarded again after they have been parsed.

# See Also:  



Example 1:

```adoscript
{% raw %}

# parse the xml string: <MAIN name="value"><SUB/></MAIN>
CC "Documentation" raw XML_SET_SCRIPT {
    PROCEDURE PARSESUB {
        CC "Documentation" XML_GET_PARENT_NODE
        CC "Documentation" XML_GET_ATTRIBUTE "name" node:(parent)
    }
}

CC "Documentation" XML_ADD_CALLBACK "PARSESUB" name:"SUB"
CC "Documentation" XML_PARSE

{% endraw %}
```
{: .line-numbers}

