---
layout: commandcall
category: CommandCall
title: "CONVERT_OBJ"
tags: 1.3 1.5
---

CONVERT_OBJ converts an object from its current class into another class, using a customized conversion function.

# Syntax:  

```adoscript
{% raw %}
CC "Core" CONVERT_OBJ objid:id TargetClass objname:strValue .

{% endraw %}
```
{: .line-numbers}

```adoscript
{% raw %}
TargetClass :	tclassid:id | tclassname:strValue .

{% endraw %}
```
{: .line-numbers}

```adoscript
{% raw %}
#-->RESULT ecode:intValue tobjid:id
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`objid`|id|
|`tclassid`|id|
|`tclassname`|strValue|
|`objname`|strValue|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`tobjid`|id|

# Remarks:

With execution of this command the related conversion function is called for the object specified with objid. The target class can be specified by ID (tclassid) or name (tclassname). Conversion functions are customized in "__Conversion__" class attributes. See see "Customizing Reference\Class Attributes\Conversion\..." for details.  
The conversion function creates a new object and deletes the existing one. The return value tobjid is the ID of the new object.

# See Also:  



Example 1:

```adoscript
{% raw %}


SET objid:(VAL objids)
CC "Core" CONVERT_OBJ objid:(objid) tclassname:"Activity"

{% endraw %}
```
{: .line-numbers}

