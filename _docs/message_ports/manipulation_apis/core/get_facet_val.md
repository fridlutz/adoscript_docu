---
layout: commandcall
category: CommandCall
title: "GET_FACET_VAL"
tags: 1.3 1.5
---

Attribute facets hold properties of attributes. GET_FACET_VAL returns the value of a specified attribute facet.

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_FACET_VAL attrid:id facetname:str .


#-->RESULT ecode:intValue val:anyValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`attrid`|id, the ID of the attribute has to be specified with attrid.|
|`facetname`|str, the name of the facet is specified with facetname.|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`val`|anyValue|

# Remarks:

Facet names  
"AttributeName"					STRING		The name of the attribute.  
See also &lt;GET_ATTR_NAME&gt;  
"AttributeType"					INTEGER		The value type code of the attribute.  
0: INTEGER  
1: DOUBLE  
2: STRING  
3: DISTRIBUTION  
4: TIME  
5: ENUMERATION  
6: ENUMERATIONLIST  
7: LONGSTRING  
8: PROGRAMCALL  
9: INTERREF  
10: EXPRESSION  
11: RECORD  
12: ATTRPROFREF  
13: DATE  
14: DATETIME  
15: CLOB  
See also &lt;GET_ATTR_TYPE&gt;.  
"AttributeValue"				any			Default attribute value.  
"EnumerationDomain"				STRING		Possible values for attributes of type  
ENUMERATION, ENUMERATIONLIST or PROGRAMCALL.  
See also &lt;GET_FACET_ENUMERATIONDOMAIN&gt;.  
"SystemAttributeFlag"			INTEGER		-- (not used)  
"MultiLineString"				INTEGER		For attributes of type STRING or LONGSTRING.  
0: single line  
1: multi line  
"AttributeHelpText"				STRING		The help text of the attribute which can be shown via the i-Button at the attribute field in  
the notebook.  
"AttributeRegularExpression"	STRING		A regular expression which limits possible values for a STRING or LONGSTRING attribute.  
"AttributeNumericDomain"		STRING		Limitation of possible values for an INTEGER or DOUBLE attribute.  
"AttributeInterRefDomain"		STRING		A LEO text defining possible targets for an INTERREF attribute.  
"RecordClassName"				STRING		The name of the class which defines the columns for a RECORD attribute.  
"RecordClassMultiplicity"		INTEGER		The number of possible rows for a RECORD attribute.  
"AttributeProfileRefDomain"		STRING		A LEO text containing the name of the table class which defines the attributes for  
an ATTRPROFREF attribute.



# See Also:  



Example:

