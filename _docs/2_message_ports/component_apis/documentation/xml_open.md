---
layout: commandcall
category: CommandCall
title: "XML_OPEN"
tags: 1.3 1.5
---

XML_OPEN opens a file for XML import or export.

# Syntax:  

```adoscript
{% raw %}
CC "Documentation" XML_OPEN	strValue [ read | write ]
							[ encoding:strValue ] 
							[ docversion: "1.0" | "1.1" ]

#--> RESULT ecode:intValue .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`<main_parameter>`|strValue, the filename of the file to which data should be exported|
|`read`|modifier, the file is opened for input/import (default).|
|`write`|modifier, the file is opened for output/export.|
|`encoding`|strValue, specifies the codepage for the output file. Possible values are "ISO8859-1", "USASCII", "WINDOWS-1252", "UTF-8", "IBM1140", "IBM037", "UTF-16[BL]E", "UCS-4[BL]E"; default is "ISO8859-1".|
|`docversion`|strValue, is used for exporting only, specifying the used XML version. The only difference between "1.0" and "1.1" is that with "1.1" control characters are masked. With "1.0" control characters are written as they are, which may result in invalid XML code.|
# Returns:  

ecode - intValue, Contains the error code or is 0 in case of success; 2 - XML_NOPARSER - another file is currently imported or exported (close it first); 4 - XML_INVALIDINPUTFILE - the file specified for importing does not exist; 8 - XML_MISSINGATTRIBUTE - no file name has been specified; 11 - XML_INITXERCES - the XML parser could not be initialized; 23 - XML_FORMATTERALREADYOPEN - another file is currently exported (close it first); 24 - XML_FILEALREADYEXISTS - the file opened for export already exists (delete it first); 25 - XML_FILECANTWRITE - the export file could not be opened; 27 - XML_ENCODINGNOTSUPPORTED - the encoding name specified is not valid.

# Remarks:



# See Also:  



Example 1:

```adoscript
{% raw %}

# open for import
CC "Documentation" XML_OPEN "models.xml" read

# open for export
CC "Documentation" XML_OPEN "output.xml" write encoding:"WINDOWS-1252"

{% endraw %}
```
{: .line-numbers}

