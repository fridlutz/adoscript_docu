---
layout: commandcall
category: CommandCall
title: "ADD_INTERREF"
tags: 1.3 1.5
---

ADD_INTERREF adds a reference to an INTERREF attribute.

# Syntax:

Add INTERREF to target by name  
```adoscript
{% raw %}
CC "Core" ADD_INTERREF 	objid:intValue attrid:intValue 
						tmodelname:strValue tmodeltype:strValue
						[ tclassname:strValue tobjname:strValue ] .
{% endraw %}
```
{: .line-numbers}

Add INTERREF to target by ID  
```adoscript
{% raw %}
CC "Core" ADD_INTERREF 	objid:intValue attrid:intValue 
						tobjid:intValue | tmodelid:intValue .
{% endraw %}
```
{: .line-numbers}

```adoscript
{% raw %}
#-->RESULT ecode:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`objid`|intValue, the ID of instance containing the attribute|
|`attrid`|intValue, the attribute to which the reference should be added|
|`tmodelname`|strValue, the name of the target model|
|`tmodeltype`|strValue, the modeltype of the target model|
|`tclassname`|strValue, the class name of the target instance|
|`tobjname`|strValue, the name of the target object|
|`tobjid`|intValue, the id of the target object|
|`tmodelid`|intValue, the id of the target model|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|

# Remarks:

Specify the attribute to which the reference should be added with the argument attrid and the instance containing the attribute with objid.

If you want to add the reference using model names, specify the model name with the argument tmodelname, the modeltype with the argument tmodeltype. If you want to add an objectreference, also specify the name of the class of the target instance with tclassname and the name of the target instance with tobjname.

If you want to add the reference using ids, specify the model id with the argument tmodelid if you want to add a modelreference or specify the object id with the argument tobjid if you want to add an objectreference.

Note:  
If the interref is created in a model (containing the instance with ID objid) which is loaded readonly, the creation of the interref fails.  
However, the returned ecode is 0, indicating success.

# See Also:  



Example 1:

This example only works for classes that contain only modelreferences. When you select an instance of a class contains an objectreference, the example will fail and return an error message.

```adoscript
{% raw %}

# get all selected objects
CC "Modeling" GET_SELECTED
IF (objids = "") {
   CC "AdoScript" ERRORBOX "No object has been selected!"
   EXIT
}

# from the list of selected objects, extract the first objectid
SET selected:(VAL token(objids,0," "))

# get the class of the selected object
CC "Core" GET_CLASS_ID objid:(selected)

# get all attributes
CC "Core" GET_ALL_ATTRS classid:(classid)

# let the user select a target modelmodelreference
CC "CoreUI" MODEL_SELECT_BOX title:"Select one model" text:(" as a target model:")

# for each attribute, check if it is an interref attribute
SET result:"Interreferences in the currently selected instance:\n\n"
FOR attrid in:(attrids) {
    CC "Core" GET_ATTR_TYPE attrid:(VAL attrid)
    CC "Core" GET_ATTR_NAME attrid:(VAL attrid)
    IF (attrtype = "INTERREF") {
        CC "Core" GET_INTERREF_TYPE objid:(selected) attrid:(VAL attrid)
        IF (type = "model") {
            # if we use tmodelid we can only handle MODREFs!
            CC "Core" ADD_INTERREF attrid:(VAL attrid) objid:(selected)
                    tmodelid:(VAL modelids)
        }
    }
}

# display the result
CC "AdoScript" INFOBOX (result)

{% endraw %}
```
{: .line-numbers}

