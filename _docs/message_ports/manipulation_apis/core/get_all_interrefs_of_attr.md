---
layout: commandcall
category: CommandCall
title: "GET_ALL_INTERREFS_OF_ATTR"
tags: 1.3 1.5
---

GET_ALL_INTERREFS_OF_ATTR returns all references of a specified INTERREF attribute value.

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_ALL_INTERREFS_OF_ATTR objid:id attrid:id .


#-->RESULT ecode:intValue reftext:references
{% endraw %}
```
{: .line-numbers}

references is a string value containing a LEO text with the following syntax:

```adoscript
{% raw %}
{ REF TargetInfo } .
{% endraw %}
```
{: .line-numbers}

```adoscript
{% raw %}
TargetInfo :	type:TargetType TargetModelInfo [ TargetObjectInfo ] .
{% endraw %}
```
{: .line-numbers}

```adoscript
{% raw %}
TargetType :	object | model .
{% endraw %}
```
{: .line-numbers}

```adoscript
{% raw %}
TargetModelInfo :	tmodeltype:strValue tmodelname:strValue
	tmodelver:strValue tmodelid:id .
{% endraw %}
```
{: .line-numbers}

```adoscript
{% raw %}
TargetObjectInfo :	tclassname:strValue tobjname:strValue
	tclassid:id tobjid:id .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`objid`|id|
|`attrid`|id|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`reftext`|references|

# Remarks:



# See Also:  



Example:

