---
layout: commandcall
category: CommandCall
title: "XML_GET_NOTEBOOK_ATTRIBUTES"
tags: 1.3 1.5
---

XML_GET_NOTEBOOK_ATTRIBUTES gets the notebook structure of the given object for the given user as a XML string.

# Syntax:  

```adoscript
{% raw %}
CC "Documentation" XML_GET_NOTEBOOK_ATTRIBUTES objid:intValue userid:intValue

#--> RESULT ecode:intValue xml:strValue.
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`objid`|intValue, the ID of the object for which the notebook structure is to be retrieved|
|`userid`|intValue, the user for which the notebook structure of the object is returned|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`xml`|strValue, string giving the notebook structure|

# Remarks:

The access rights (as possibly specified by SET_ACCESS in the ATTRREP definition for the usergroup of the user) is taken into account.  
I.e. attributes to which the user has no access, will not be contained in the returned XML string.

The following schema is used  
```adoscript
{% raw %}
<?xml version="1.0" encoding="UTF-8"?>
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"
            targetNamespace="@boc-eu.com/boc-is/adonis.notebook.document;1"
            xmlns="@boc-eu.com/boc-is/adonis.notebook.document;1"
            xmlns:repoxml="@boc-eu.com/boc-is/adonis.notebook.document;1"
            xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
            elementFormDefault="qualified">
<xsd:element name="notebook">
  <xsd:complexType>
    <xsd:sequence>
      <xsd:element ref="chapter" minOccurs="0" maxOccurs="unbounded" />
    </xsd:sequence>
  </xsd:complexType>
</xsd:element>

<xsd:element name="chapter">
  <xsd:complexType>
    <xsd:sequence>
      <xsd:element ref="group" minOccurs="0" maxOccurs="unbounded" />
      <xsd:element ref="attribute" minOccurs="0" maxOccurs="unbounded" />
    </xsd:sequence>
    <xsd:attribute name="name" type="xsd:string"  use="required" />
  </xsd:complexType>
</xsd:element>

<xsd:element name="group">
  <xsd:complexType>
    <xsd:sequence>
      <xsd:element ref="attribute" minOccurs="0" maxOccurs="unbounded" />
    </xsd:sequence>
    <xsd:attribute name="name" type="xsd:string"  use="required" />
  </xsd:complexType>
</xsd:element>

<xsd:element name="attribute">
  <xsd:complexType>
    <xsd:attribute name="id" type="xsd:string" use="required" />
    <xsd:attribute name="name" type="xsd:string"  use="required" />
    <xsd:attribute name="write-protected" type="xsd:string"  use="required" />
  </xsd:complexType>
</xsd:element>

</xsd:schema>

{% endraw %}
```
{: .line-numbers}
# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Modeling" GET_SELECTED
CC "UserMgt" GET_USER_ID_OF_CURRENT_USER
SET objid:(VAL token (objids, 0, " "))
CC "Documentation" XML_GET_NOTEBOOK_ATTRIBUTES objid:(objid) userid:(userid)
CC "AdoScript" EDITBOX text:(xml)

{% endraw %}
```
{: .line-numbers}

