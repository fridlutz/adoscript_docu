---
layout: commandcall
category: CommandCall
title: "ACFILTER_GFX_DISABLE"
tags: 1.3 1.5
---

ACFILTER_GFX_DISABLE disables the usage of the attribute and class filter for graphics.

# Syntax:  

```adoscript
{% raw %}
CC "Documentation" ACFILTER_GFX_DISABLE	attribute:strValue

#--> RESULT ecode:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`attribute`|strValue, the name of the attribute|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|

# Remarks:

Calling this command has the same effect as unchecking the checkbox "Use attribute and class filter for graphics" in the dialog "attribute and class filter" dialog.

This command has no effect when the attribute and class filter is disabled.

# See Also:  

[ACFILTER_ENABLE](acfilter_enable.html "ACFILTER_ENABLE")  
[ACFILTER_DISABLE](acfilter_disable.html "ACFILTER_DISABLE")  
[ACFILTER_GFX_ENABLE](acfilter_gfx_enable.html "ACFILTER_GFX_ENABLE")  


Example 1:

```adoscript
{% raw %}

CC "Documentation" ACFILTER_GFX_DISABLE attribute:"Attribute and Class Filter"

{% endraw %}
```
{: .line-numbers}

