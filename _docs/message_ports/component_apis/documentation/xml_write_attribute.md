---
layout: commandcall
category: CommandCall
title: "XML_WRITE_ATTRIBUTE"
tags: 1.3 1.5
---

XML_WRITE_ATTRIBUTE writes an attribute into the current (last opened) node.

# Syntax:  

```adoscript
{% raw %}
CC "Documentation" XML_WRITE_ATTRIBUTE	strValue value:strValue 

#--> RESULT ecode:intValue 
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`<main_parameter>`|strValue, the name of the attribute.|
|`value`|strValue, the attribute value.|

# Returns:  

ecode - intValue, Contains the error code or is 0 in case of success; 8 - XML_MISSINGATTRIBUTE - no name has been specified; 26 - XML_ATTRIBUTEOUTSIDENODE - this has to be called right after XML_WRITE_START_NODE! 28 - XML_NOFORMATTER - no file has yet been opened for writing.

# Remarks:

This has to be called right after XML_WRITE_START_NODE or XML_WRITE_ATTRIBUTE.

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Documentastion" XML_OPEN "test.xml" write
CC "Documentation" XML_WRITEPLAIN "<?xml version=\"1.0\" encoding=\"iso-8859-1\"?>"
CC "Documentation" XML_WRITE_START_NODE "MODEL"
CC "Documentation" XML_WRITE_ATTRIBUTE "type" value:"gp"
CC "Documentation" XML_WRITE_CONTENT "Ein Modell"
CC "Documentation" XML_WRITE_END_NODE "MODEL"
CC "Documentation" XML_CLOSE write
#
# produced the follofing file:
# <?xml version=\"1.0\" encoding=\"iso-8859-1\"?>
# <MODEL type="gp">Ein Modell</MODEL>
#   

{% endraw %}
```
{: .line-numbers}

