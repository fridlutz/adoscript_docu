---
layout: commandcall
category: CommandCall
title: "XML_DISPLAYERROR"
tags: 1.3 1.5
---

XML_DISPLAYERROR shows an error message, if an error occured.

# Syntax:  

```adoscript
{% raw %}
CC "Documentation" XML_DISPLAYERROR	[ hide ]
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`hide`|modifier, if passed the message wont be displayed, but just logged.|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success|

# Remarks:

If the last call to the XML parser returned XML_NOERROR, this method does nothing.

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Documentation" XML_OPEN "FileThatNotExists.Xml"
CC "Documentation" XML_DISPLAYERROR

{% endraw %}
```
{: .line-numbers}

