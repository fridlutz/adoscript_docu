---
layout: commandcall
category: CommandCall
title: "GET_REFERENCED_ATTRPROF_VERSION_ID"
tags: 1.3 1.5
---

GET_REFERENCED_ATTRPROF_VERSION_ID determines the ID of a referenced Attribute Profile in the given attribute of the given object.

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_REFERENCED_ATTRPROF_VERSION_ID modelid:intValue objid:intValue attrid:intValue


#-->RESULT ecode:intValue apversionid:intValue apthreadname:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|intValuem, the parameter modelid must specifiy the ID of the source model.|
|`objid`|intValue, the parameter objid must specify the ID of the object model.|
|`attrid`|intValue, the parameter attrid must specify the ID of the source attribute which must be of type CORE_ATTRPROFREF.|

# Returns:  

|`ecode`|intValue, the return variable ecode is set to 0 if the command succeeded.|
|`apversionid`|intValue, the return variable apversionid contains the ID of the referenced AP version. If no AP is referenced the value is -1.|
|`apthreadname`|strValue, the return variable apthreadname contains the name of the referenced AP thread. If no AP is referenced, the value contains an empty string.|

# Remarks:

If ecode is INVALID_ATTRPROF_VERSION you are referencing a non existing AP. If ecode is ATTRIBUTE_NOT_EXISTING you tried to call this command with an invalid model/instance/attribute ID! Any other error code means that the reference string is invalid!



# See Also:  



Example 1:

```adoscript
{% raw %}

SEND "GET_ACTIVE_MODEL" to:"Modeling" answer:modelid
IF (modelid = "")
{
  CC "AdoScript" ERRORBOX "Open a model first"
  EXIT
}

CC "Core" GET_CLASS_ID classname:"Klasse mit allen Attributtypen"
IF (ecode != 0)
{
  CC "AdoScript" ERRORBOX "Your library does not contain a class called Aktivität!\n"
  EXIT
}

CC "Core" GET_OBJ_ID modelid:(VAL modelid) classid:(classid) objname:"Sepp"
IF (ecode != 0)
{
   CC "AdoScript" INFOBOX ("Your model does not contain an 'Klasse mit allen Attributtypen' 'Sepp'!\n"+
                           "Please model one and then rerun the script.")
  EXIT
}

CC "Core" GET_ATTR_ID classid:(classid) attrname:"Attributprofilreferenz für Test"
IF (ecode != 0)
{
  CC "AdoScript" INFOBOX "no such attr 'Attributprofilreferenz für Test'"
  EXIT
}

CC "Core" debug GET_REFERENCED_ATTRPROF_VERSION_ID modelid:(VAL modelid) objid:(objid) attrid:(attrid)

{% endraw %}
```
{: .line-numbers}

