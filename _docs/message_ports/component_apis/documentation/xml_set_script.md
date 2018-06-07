---
layout: commandcall
category: CommandCall
title: "XML_SET_SCRIPT"
tags: 1.3 1.5
---

XML_SET_SCRIPT sets the callback procedures for SAX parsing an XML file.

# Syntax:  

```adoscript
{% raw %}
CC "Documentation" XML_SET_SCRIPT { AdoScriptInline }

CC "Documentation" XML_SET_SCRIPT AdoScriptAsStr
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`AdoScriptInline	`|direct (inline) AdoScript code.|
|`AdoScriptAsStr`|strValue, is a string constant or string variable containing an AdoScript.|


# Returns:  

ecode - intValue, Contains the error code or is 0 in case of success; 3 - XML_NOPARSER - a file has to be opened first; 6 - XML_SCRIPTALREADYSET - XML_SET_SCRIPT has already been called; 7 - XML_LEOPARSERERROR - the procedure definitions passed contain leo-syntax errors; 8 - XML_MISSINGATTRIBUTE - no AdoScript has been passed.

# Remarks:

This method can only be called once. The script can either be appended inline (in curly brackets {}) or passed as string argument. See example for how to do it.

The used XSD schema is listed below.

# See Also:  



Example 1:

```adoscript
{% raw %}

# either append the script in brackets {}
CC "Documentation" raw XML_SETSCRIPT {
    PROCEDURE CREATEMODEL name:string id:int {
        # some adoscript here
    }
    PROCEDURE CREATEATTRIBUTE name:string id:int {
        # some other adoscript here
    }
}
# or set it with an argument
CC "AdoScript" FREAD file:"xmlimp.leo"
CC "Documentation" XML_SETSCRIPT (text)

{% endraw %}
```
{: .line-numbers}

