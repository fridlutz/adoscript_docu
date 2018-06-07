---
layout: commandcall
category: CommandCall
title: "GET_INCOMING_INTERREFS"
tags: 1.3 1.5
---

GET_INCOMING_INTERREFS returns all incoming inter-references to a model or to a modeling object.

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_INCOMING_INTERREFS Target [ sourcemodelids:strValue ] .

{% endraw %}
```
{: .line-numbers}

```adoscript
{% raw %}
Target :	objid:intValue | modelid:intValue .
{% endraw %}
```
{: .line-numbers}

```adoscript
{% raw %}
#-->RESULT ecode:intValue reftext:references
{% endraw %}
```
{: .line-numbers}

references is a string value containing a LEO text with the following syntax:

```adoscript
{% raw %}
{ REF SourceInfo TargetInfo } .
{% endraw %}
```
{: .line-numbers}

```adoscript
{% raw %}
SourceInfo :	srcmodelid:id srcobjid:id srcclassid:id srcattrid:id
	srcownerid:id srcownerattrid:id srcobjname:strValue .
{% endraw %}
```
{: .line-numbers}

```adoscript
{% raw %}
TargetInfo :	targettype:TargetType TargetModelInfo [ TargetObjectInfo ] .
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
TargetModelInfo :	tmodeltype:strValue tversion:strValue .
{% endraw %}
```
{: .line-numbers}

```adoscript
{% raw %}
TargetObjectInfo :	tclassname:strValue tobjname:strValue .
{% endraw %}
```
{: .line-numbers}


# Parameters:  

Target
|`sourcemodelids`|strValue|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`reftext`|references|

# Remarks:

If you want to get incoming object references, the object id has to be passed as argument objid. If you want to compute incoming model references, the id of the model has to be passed in the argument modelid.

The inter-references are returned as LEO string containing:  
Source model ID:					srcmodelid  
Source object ID:					srcobjid  
Source class ID:					srcclassid  
Source attribute ID:				srcattrid  
Source owner object ID:				srcownerid  
Source owner attribute ID:			srcownerattrid  
Source object name:					srcobjname  
Type of the target:					targettype (either object or model)  
Model type of the target model:		tmodeltype  
Model name of the target model:		tmodelname  
Target version number:				tversion  
Target class name:					tclassname  
Target object name:					tobjname

The source object is always the instance which is the direct outgoing point of a reference. When a reference is outgoing from a record cell, the source object (srcobjid) is a record row and the sorce attribute (srcattrid) is a record column. In that case, the modeling object containing the record can be determined with srcownerid, while the record attribute can be determined with srcownerattrid. Otherwise, when the outgoing point of a reference is a modeling object, srcownerid equals srcobjid, while srcowneratrid equals srcattrid. The value of srcobjname is always the name of the modeling instance, even if the source object is a record row.

Note that targettype is not specified as string but as modifier. So, if the target type shall be extracted using the  LEO command, get-modifier has to be used here.

With the optional string parameter sourcemodelids the result can be filtered, so that only references from certain source models are returned. The string contains model IDs separated by " " (blank). If sourcemodelids is not specified, no filtering is applied. Otherwise only those references are returned which are outgoing from one of the models which are contained as ID in the string.

# See Also:  



Example:

