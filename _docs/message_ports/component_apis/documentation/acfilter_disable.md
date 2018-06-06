---
layout: commandcall
category: CommandCall
title: "ACFILTER_DISABLE"
tags: 1.3 1.5
---

ACFILTER_DISABLE disables the attribute and class filter.

# Syntax:  

```adoscript
{% raw %}
CC "Documentation" ACFILTER_DISABLE	attribute:strValue

#--> RESULT ecode:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`attribute`|strValue, the name of the attribute|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success|

# Remarks:

Calling this command has the same effect as unchecking the checkbox "Use settings of attribute and class filter" in the dialog "attribute and class filter" dialog.


# See Also:  

[ACFILTER_ENABLE](acfilter_enable.html "ACFILTER_ENABLE")  


Example 1:

```adoscript
{% raw %}

CC "Documentation" ACFILTER_ENABLE
CC "Documentation" EXEC_ACFILTER
        attribute:"Attribute and Class Filter"
        modeltype:"Sample Target Model"
CC "Documentation" ACFILTER_DISABLE
CC "Documentation" EXEC_ACFILTER
        attribute:"Attribute and Class Filter"
        modeltype:"Sample Target Model"

{% endraw %}
```
{: .line-numbers}

First enables the attribute and class filter. In the second command the attribute and class filter dialog is executed. Note that the checkbox "Use attribute and class filter settings" is checked. The third command disables the attribute and class filter. The forth command executes the dialog again with the checkbox not checked.  
