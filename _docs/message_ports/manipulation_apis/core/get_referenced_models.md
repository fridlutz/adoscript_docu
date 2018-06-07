---
layout: commandcall
category: CommandCall
title: "GET_REFERENCED_MODELS"
tags: 1.3 1.5
---

GET_REFERENCED_MODELS returns a list of IDs of referenced models.

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_REFERENCED_MODELS modelid:id references:{ References } .

{% endraw %}
```
{: .line-numbers}

```adoscript
{% raw %}
References :	{ From } .
{% endraw %}
```
{: .line-numbers}

```adoscript
{% raw %}
From :	FROM modelTypeName { Follow } .
{% endraw %}
```
{: .line-numbers}

```adoscript
{% raw %}
Follow :	FOLLOW classname:classname attrname:attrname
	[ recattrname:recordattrname ]
	depth:intValue type:RefFollowType .
{% endraw %}
```
{: .line-numbers}

```adoscript
{% raw %}
RefFollowType :	main | sub .
{% endraw %}
```
{: .line-numbers}

```adoscript
{% raw %}
#-->RESULT modelids:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|id, the ID of the source model has to be passed as argument modelid.|
|`references`|{ References }|

# Returns:  

|`modelids`|strValue|

# Remarks:

GET_REFERENCED_MODELS computes all models referenced by the source model and returns a list of referenced model IDs as variable modelids.

With the reference argument, you have to define a reference profile. A reference profile describes which references shall be followed: It contains a list of INTERREF attributes and for each INTERREF attribute a specification, if and how the reference should be followed.

The reference argument corresponds to the list in the ADOxx dialog "Reference settings": For each modeltype, the keyword FROM followed by a modeltype is entered. After the modeltype definition, for each interref attribute, the keyword FOLLOW is entered. The class that owns the interref attribute is specified with the argument classname, the interref attribute itself is specified with attrname. If the attribute is within a record attribute, the name of the record attribute has to be specified with recattrname. The depth canm be set with the argument depth, set it to the value -1 for the value "unlimited". Set the argument type to main if the interref should be treated as a main reference or set it to sub if it should be treated as a sub reference.

Unfortunately this command does not return an error code.

Please Note:  
If classname is ambiguos within the Application Library, i.e. there is one class with the name classname in the BP library and an other one with the same name in the WE library, the corresponding class can not be determined unambigously. In that case ADOxx tries to evaluate the command for the class whichever is found first in the application library, resulting in unpredictable behavior.

# See Also:  



Example 1:

```adoscript
{% raw %}

# note: if you are using this example in a language different than 
# German, adjust modeltype, class and attribute names!

# get the currently opened model
CC "Modeling" GET_ACT_MODEL
IF (modelid = -1) {
    CC "AdoScript" ERRORBOX "Open a Geschäftsprozeßmodell first!"
    EXIT
}

# get all referenced models
CC "Core" GET_REFERENCED_MODELS modelid:(modelid)
    references:{
        FROM "Geschäftsprozeßmodell"
        FOLLOW classname:"Aktivität" attrname:"Referenzierte Dokumente"
               depth:-1 type:main
        FOLLOW classname:"Prozeßaufruf" attrname:"aufgerufener Prozeß"
               depth:-1 type:main
    }

# finally open every referenced model in the modeling shell
FOR id in:(modelids) {
    CC "Modeling" OPEN modelids:(id)
}

{% endraw %}
```
{: .line-numbers}

