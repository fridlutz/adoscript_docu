---
layout: commandcall
category: CommandCall
title: "XML_GET_VALUE"
tags: 1.3 1.5
---

XML_GET_VALUE returns the value of an XML element.

# Syntax:  

```adoscript
{% raw %}
CC "Documentation" XML_GET_VALUE [ node:intValue ]

#--> RESULT ecode:intValue value:strValue .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`node`|intValue, ID of another element than the current for which to get an attribute. If no node is specified, the current node is queried.|

# Returns:  

ecode - intValue, Contains the error code or is 0 in case of success; 3 - XML_NOPARSER - a file has to be opened first; 15 - XML_NODENOTEXISTING - the element with the specified id is not existing are already discarded from memory;
|`value`|strValue, contains the value of the given XML element.|

# Remarks:

Called within a callback procedure.

The value can only be obtained to the point in the file that is currently parsed. If the XML_GET_VALUE is called before the end node of the XML element has been parsed the returned value may be incomplete or empty.

Also values of other elements than the current can be queried. But values are only returned when the element is currently held in memory. If for example an element that has not yet been parsed or an element that has already been parsed but discarded again is queried, an error code will be returned. By default all elements that have no child elements are discarded again after they have been parsed.

# See Also:  



Example 1:

```adoscript
{% raw %}

# parse the xml string: <MAIN>Line 1<SUB/>Line 2</MAIN>
CC "Documentation" raw XML_SET_SCRIPT {
    PROCEDURE PARSESUB {
        CC "Documentation" XML_GET_PARENT_NODE
        CC "Documentation" XML_GET_VALUE node:(parent)
        # will return only "Line 1" because the text
        # "Line 2" has not yet been parsed
    }
}
CC "Documentation" XML_ADD_CALLBACK "PARSESUB" name:"SUB"
CC "Documentation" XML_PARSE

{% endraw %}
```
{: .line-numbers}

