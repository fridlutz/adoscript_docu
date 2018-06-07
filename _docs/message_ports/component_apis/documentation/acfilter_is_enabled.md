---
layout: commandcall
category: CommandCall
title: "ACFILTER_IS_ENABLED"
tags: 1.3 1.5
---

ACFILTER_IS_ENABLED returns whether the attribute and class filter is enabled or disabled.

# Syntax:  

```adoscript
{% raw %}
CC "Documentation" ACFILTER_IS_ENABLED attribute:strValue

#--> RESULT ecode:intValue enabled:boolValue 
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`attribute`|strValue, the name of the attribute|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success|
|`enabled`|1|0, is 1 if the AC filter is enabled and 0 if it is disabled.|

# Remarks:



# See Also:  

[ACFILTER_GFX_IS_ENABLED](acfilter_gfx_is_enabled.html "ACFILTER_GFX_IS_ENABLED")  
[ACFILTER_DISABLE](acfilter_disable.html "ACFILTER_DISABLE")  
[ACFILTER_ENABLE](acfilter_enable.html "ACFILTER_ENABLE")  


Example 1:

```adoscript
{% raw %}

CC "Documentation" ACFILTER_IS_ENABLED attribute:"Attribut- und Klassenfilter"
SET s:"The attribute and class filter is %enabled."
SET s:(replace(s, "%", cond(enabled, "", "not ")))
CC "AdoScript" INFOBOX (s)

{% endraw %}
```
{: .line-numbers}

