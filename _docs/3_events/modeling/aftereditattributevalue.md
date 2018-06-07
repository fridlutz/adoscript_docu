---
layout: event
category: Event
title: "AfterEditAttributeValue"
tags: 1.3 1.5
---

This event is triggered when an attribute value has been edited in a notebook, in the tabular modeling or via a "quick edit" field on the drawing area.  

# Parameters:  

|`instid`|intValue, the ID of the changed instance.|
|`attrid`|intValue, the Attribute ID.|
|`modelid`|intValue, the ID of the model containing the changed instance.|
|`attrtypeid`|intValue, the Attribute type code as follows: 0 INTEGER, 1 DOUBLE, 2 STRING, 3 DISTRIBUTION, 4 TIME, 5 ENUMERATION, 6 ENUMERATIONLIST, 7 LONGSTRING, 8 PROGRAMCALL, 9 INTERREF, 10 EXPRESSION, 11 RECORD, 12 ATTRPROFREF, 13 DATE, 14 DATETIME, 15 CLOB|

Exit value:



# Remarks:  

It is similar to the "SetAttributeValue" event. The difference is, that attribute value changes which are not initiated by the user, e.g. by import, trigger a "SetAttributeValue" event, but not an "AfterEditAttributeValue" event.

An "AfterEditAttributeValue" event is always triggered later than the corresponding "SetAttributeValue" event.  

# See Also:  



Example:  
```adoscript
{% raw %}
  
  ON_EVENT "AfterCreateModelingConnector" 
{ 
SETG n_currModeld: (modelid)
SETG n_relClassId: (classid)
SETG n_relObjId: (objid)
SETG n_fromObjId: (fromobjid)
SETG n_toObjId: (toobjid)

  
#n_currModeld   : the model ID of the modified model, 
#n_relObjId     : the ID of the newly inserted instance, 
#n_relClassId   : the ID of this instance's class, 
#n_fromObjId : the ID of the from-object of the new connector, 
#n_toObjId   : the ID of the new connector's target object 


#Get the "Type" attribute value of from object
CC "Core"  GET_ATTR_VAL objid: (n_fromObjId) attrname: ("Type")

#--> RESULT ecode: intValue val: anyValue 

SET s_fromObjType: (val)

#Get the "Type" attribute value of from object
CC "Core"  GET_ATTR_VAL objid: (n_toObjId) attrname: ("Type")

#--> RESULT ecode: intValue val: anyValue 

SET s_toObjType: (val)
SET s_Selections: ("Do nothing@Correct Automatically")
# if attribute value of from object is "RF" and attribute value of to object is "DRF" throw exception and offer possible solutions
IF (s_fromObjType = ("RF") AND s_toObjType = ("DRF") )
{
	 CC "AdoScript" LISTBOX entries: (s_Selections) toksep:"@" title: ("Select a Option") oktext: "Select"
		

	#--> RESULT endbutton: strValue selection: strValue [ extraValues ] . 
	 SET s_Selection: (selection)
	 
	 #if selection is "Correct Automatically" delete erroneous connector and create correct one
	 IF (s_Selection =("Correct Automatically"))
	 {

		 CC "Core"  DELETE_CONNECTOR modelid: (n_currModeld) objid: (n_relObjId)

		 CC "Core"  CREATE_CONNECTOR modelid: (n_currModeld) fromobjid: (n_toObjId) toobjid: (n_fromObjId) classid: (n_relClassId)

		#--> RESULT ecode: intValue objid: id . 
	 }

		# else throw exception and  delete erroneous connector
	ELSE 
	{
		CC "AdoScript" ERRORBOX ("Relation from Rule Family type of RF to Rule Family type of DRF is not allowed")
		CC "Core"  DELETE_CONNECTOR modelid: (n_currModeld) objid: (n_relObjId)
	}

 
}
}
{% endraw %}
```
{: .line-numbers}
