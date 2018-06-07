---
layout: commandcall
category: CommandCall
title: "GENERATE_LIBRARY_SGML"
tags: 1.3 1.5
---

GENERATE_LIBRARY_SGML generates a sgml file of the given application library containing the content of the library (libraryattributes, (relation)classes and their attributes). Additionally graphic files (png) containing the class graphreps will be generated. The generated sgml file can e.g. be used as an input for a method manual.

# Syntax:  

```adoscript
{% raw %}
CC "Application" GENERATE_LIBRARY_SGML libid:intValue filename:strValue [ filetype: sgml | xml ]
										[ with-namedgfx ] [ replacechar:strValue ]
										[ resolve-directives[:boolValue] ]

#--> RESULT ecode:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`libid`|intValue, the ID of the application library.|
|`filename`|strValue, the name of the sgml file to be generated (full path).|
|`filetype`| sgml | xml, export file type. The default file type is SGML. When filetype:xml is specified, the export file is in XML format. This is similar to SGML. However, all tags are closed and the encoding is always UTF8.|
|`with-namedgfx`|modifier, if this is given, additionally icon files for the classes and named like the classes will be generated. If this option is given, all graphic files will have the format bmp.|
|`replacechar`|strValue, the character replacing invalid characters in filenames. This makes only sense, if also with-namedgfx is given. As a class might contain characters which result in invalid Windows file names, those invalid characters are replaced by the given one. If no replacechar is given, "_" is used. The invalid characters are: "**\/:&lt;&gt;?||
|`resolve-directives`|boolValue, with this option being activated, @INCLUDE directives in LEO attributes are resolved automatically. This makes it possible for simple LEO parsers to parse the effective LEO text. However, export files with resolved includes will usually not be importable by ADOxx (because of too long string attribute values).|

# Returns:  

|`ecode`|intValue, contains the error code or is 0 in case of success.|

# Remarks:

This command is available only in the ADOxx Development Toolkit.

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Core" GET_LIB_ID libname:"ADOxx Experimentation Library 1.3UL1"
CC "Core" LOAD_LIB libid:(libid)
CC "Application" GENERATE_LIBRARY_SGML libid:(libid)
        filename:"d:\\temp\\b\\b.xml" filetype:xml resolve-directives
CC "Application" EXIT

{% endraw %}
```
{: .line-numbers}

