---
layout: commandcall
category: CommandCall
title: "ACFILTER_GFX_ENABLE"
tags: 1.3 1.5
---

ACFILTER_GFX_ENABLE enables the usage of the attribute and class filter for graphics.

# Syntax:  

```adoscript
{% raw %}
CC "Documentation" ACFILTER_GFX_ENABLE attribute:strValue

#--> RESULT ecode:intValue .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`attribute`|strValue, the name of the attribute|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|

# Remarks:

Calling this command has the same effect as checking the checkbox "Use attribute and class filter for graphics" in the dialog "attribute and class filter" dialog.

This command has no effect when the attribute and class filter is disabled.

# See Also:  

[ACFILTER_ENABLE](acfilter_enable.html "ACFILTER_ENABLE")  
[ACFILTER_DISABLE](acfilter_disable.html "ACFILTER_DISABLE")  
[ACFILTER_GFX_DISABLE](acfilter_gfx_disable.html "ACFILTER_GFX_DISABLE")  


Example 1:

```adoscript
{% raw %}

CC "Documentation" ACFILTER_GFX_ENABLE attribute:"Attribute and Class Filter"

{% endraw %}
```
{: .line-numbers}

