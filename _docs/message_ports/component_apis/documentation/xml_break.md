---
layout: commandcall
category: CommandCall
title: "XML_BREAK"
tags: 1.3 1.5
---

XML_BREAK stops the parsing.

# Syntax:  

```adoscript
{% raw %}
CC "Documentation" XML_BREAK
{% endraw %}
```
{: .line-numbers}

# Parameters:  

none

# Returns:  

none

# Remarks:

This method can be called within a callbackprocedure to abort the xml import. When it is called, the parsing of the xml file will stop at once and an error code will be returned by XML_PARSE.

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Documentation" XML_SETSCRIPT raw {
   PROCEDURE CREATEMODEL name:string id:int {
      # some adoscript here
      CC "Documentation" XML_BREAK
   }
}

{% endraw %}
```
{: .line-numbers}

