---
layout: commandcall
category: CommandCall
title: "GET_DANGLING_INTERREFS_OF_AP"
tags: 1.3 1.5
---

GET_DANGLING_INTERREFS_OF_AP retrieves all broken outgoing references of the AttrProf version specified by apversionid.

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_DANGLING_INTERREFS_OF_AP apversionid:intValue .


#-->RESULT ecode:intValue reftext:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`apversionid`|intValue|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`reftext`|strValue|

# Remarks:


The return variable reftext contains a string which contains 0 to n lines of the following code:

```adoscript
{% raw %}
REF srcmodelid - intValue
    srcdobjid - intValue
    srcattrid - intValue
    srcobjname - strValue
    targettype - strValue
    tmodeltype - strValue
    tmodelname - strValue
    tversion - strValue
    tclassname - strValue
    tobjname - strValue '\n'
{% endraw %}
```
{: .line-numbers}

targettype is either "model" or "object" depending on whether you have reference to a model (model reference) or a reference to an object in a model (instance reference).  
If targettype is "model" you can ignore the variables tclassname and tobjname since they always contain an empty string ("").

# See Also:  



Example:

