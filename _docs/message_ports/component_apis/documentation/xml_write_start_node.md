---
layout: commandcall
category: CommandCall
title: "XML_WRITE_START_NODE"
tags: 1.3 1.5
---

XML_WRITE_START_NODE writes a start node.

# Syntax:  

```adoscript
{% raw %}
CC "Documentation" XML_WRITE_STARTNODE	strValue 

#--> RESULT ecode:intValue .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`<main_parameter>`|strValue, the name of the node|

# Returns:  

ecode - intValue, Contains the error code or is 0 in case of success; 8 - XML_MISSINGATTRIBUTE - no name has been specified.; 28 - XML_NOFORMATTER - no file has yet been opened for writing.

# Remarks:



# See Also:  

[XML_WRITE_END_NODE](xml_write_end_node.html "XML_WRITE_END_NODE")  


Example 1:

```adoscript
{% raw %}

CC "Documentation" XML_OPEN "test.xml" write
CC "Documentation" XML_WRITEPLAIN "<?xml version=\"1.0\" encoding=\"iso-8859-1\"?>"
CC "Documentation" XML_WRITE_START_NODE "MODEL"
CC "Documentation" XML_WRITE_ATTRIBUTE "type" value:"gp"
CC "Documentation" XML_WRITE_CONTENT "Ein Modell"
CC "Documentation" XML_WRITE_END_NODE "MODEL"
CC "Documentation" XML_CLOSE write

# produced the follofing file:
# <?xml version=\"1.0\" encoding=\"iso-8859-1\"?>
# <MODEL type="gp">Ein Modell</MODEL>

{% endraw %}
```
{: .line-numbers}

