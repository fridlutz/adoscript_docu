---
layout: commandcall
category: CommandCall
title: "EXEC_ACFILTER"
tags: 1.3 1.5
---

EXEC_ACFILTER starts the attribute class filter dialog.

# Syntax:  

```adoscript
{% raw %}
CC "Documentation" EXEC_ACFILTER attribute:strExpr [modeltype:strValue]
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`attribute`|strExpr, must contain the name of a string (or longstring) classattribute in the bp class "__LibraryMetaData__".|
|`modeltype`|strValue, is passed if you want to preselect a special model type.|

# Returns:  

none

# Remarks:



# See Also:  



Example 1:

Starts the attribute and class filter dialog and preselects the model type "Target Sample Model". Stores the settings made by the user in the attribute "Attribute and Class Filter".  
```adoscript
{% raw %}

CC "Documentation" EXEC_ACFILTER attribute:"Attribute and Class Filter" modeltype:"Target Sample Model"

{% endraw %}
```
{: .line-numbers}

