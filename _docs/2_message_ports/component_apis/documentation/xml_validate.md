---
layout: commandcall
category: CommandCall
title: "XML_VALIDATE"
tags: 1.3 1.5
---

XML_VALIDATE validates the XML file.

# Syntax:  

```adoscript
{% raw %}
CC "Documentation" XML_VALIDATE

#--> RESULT ecode:intValue 
{% endraw %}
```
{: .line-numbers}

# Parameters:  

none

# Returns:  

ecode - intValue, contains the error code or is 0 in case of success; 3 - XML_NOPARSER - a file has to be opened first; 12 - XML_PARSINGGENERAL an error occured while parsing the xml file; 13 - XML_PARSINGXMLFILE - an error occured within the xml file.

# Remarks:

A DTD has to be referenced within the XML file, otherwise the XML file will always be invalid. Validation is done by parsing the file once. When the parser encounters an element not conformant to the DTD, it aborts and returns an error code.

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Documentation" XML_OPEN "file.xml"
CC "Documentation" XML_VALIDATE
IF (ecode = 13) {
    CC "AdoScript" INFOBOX "Invalid xml file!"
}

{% endraw %}
```
{: .line-numbers}

