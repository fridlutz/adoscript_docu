---
layout: commandcall
category: CommandCall
title: "RESET_NUMBERING"
tags: 1.3 1.5
---



# Syntax:  

```adoscript
{% raw %}
CC "Modeling" RESET_NUMBERING [ modelid:intValue]


# --> RESULT ecode:intValue

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|intValue|

# Returns:  

|`ecode`|intValue, the returned ecode is 0 if the command has been executed successfully. If there was an error an ecode of 1 is returned.|


# Remarks:

This AdoScript command performs a reset of a simple numbering, i.e. attribute values are set back to 0 or empty string.  
Which value is set depends on the type of the numbered attribute. For each object the numbered attribute is given by the value of the classattribute SortAttr.  
The attribute defined there must be writable, also in the notebook of the class and of numeric or string type (CORE_INTEGER, CORE_DOUBLE, CORE_STRING, CORE_LONGSTRING).  
If the attribute is of numeric type, RESET_NUMBERING will set the value back to 0.  
If the attribute is of string type, RESET_NUMBERING will set the value back to an empty string.  
This works for all modeltypes and all classes in each library (if the conditions above concerning SortAttr are met).

If the input parameter modelid is given this model numbering is resetted, otherwise the active model is resetted.




# See Also:  



Example 1:

```adoscript
{% raw %}

# reset possible previous instance numbers in the current model
CC "Modeling" RESET_NUMBERING

{% endraw %}
```
{: .line-numbers}


