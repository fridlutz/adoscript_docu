---
layout: commandcall
category: CommandCall
title: "XML_PARSE"
tags: 1.3 1.5
---

XML_PARSE starts parsing the opened XML file.

# Syntax:  

```adoscript
{% raw %}
CC "Documentation" XML_PARSE [ validate ]

#--> RESULT ecode:intValue parseduration:intValue 
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`validate`|modifier, validate the file while parsing (a dtd has to be referenced within the parsed file). If the file does not correspond to this dtd, the parsing will be aborted and an error code returned.|


# Returns:  

ecode - intValue, Contains the error code or is 0 in case of success; 3 - XML_NOPARSER - a file has to be opened first; 12 - XML_PARSINGGENERAL - an error occured while parsing the xml file; 13 - XML_PARSINGXMLFILE - an error occured within the xml file (e.g. inconsistent element to dtd); 22 - XML_USERBREAK - XML_BREAK has been called within a callback procedure.
|`parseduration `|intValue, the time which was spent parsing the file in ms.|

# Remarks:

The XML file is read from beginning to end. Every time an XML element is encountered the parser checks if a callback procedure has been registered for that element. If so, the procedure is executed before the parsing of the XML file is continuted.

# See Also:  



Example 1:

```adoscript
{% raw %}

# ...
CC "Documentation" XML_PARSE validate

{% endraw %}
```
{: .line-numbers}

