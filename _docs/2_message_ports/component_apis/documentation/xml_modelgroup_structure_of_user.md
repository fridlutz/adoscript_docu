---
layout: commandcall
category: CommandCall
title: "XML_MODELGROUP_STRUCTURE_OF_USER"
tags: 1.3 1.5
---

XML_MODELGROUP_STRUCTURE_OF_USER generates an XML file giving model group structure and models for a given user.

# Syntax:  

```adoscript
{% raw %}
CC "Documentation" XML_MODELGROUP_STRUCTURE_OF_USER userid:intValue 

#--> RESULT ecode:intValue xml:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`userid`|intValue, the id of a user to be used to get the model group structure and models.|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success|
|`xml`|strValue, contains the resulting xml string.|

# Remarks:

Please note that if the userid has different permissions than the user running the command then the returned information will be filtered to the lowest level. Even if the user running the command can read/write an attribute, but the userid can not, then the attribute will not be returned in the XML.

For the XML attribute "grouppermission" and "modelpermission" the corresponding value is returned in the logged in language.

The XML attribute values, "write" or "read", give the permission of the user for the attribute.

As long as the corresponding lrc files have been translated into the local language then a local version of the strings would be returned.

The following XML schema will be used.  
```adoscript
{% raw %}
<?xml version="1.0" encoding="UTF-8"?>

<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"
            targetNamespace="@boc-eu.com/boc-is/adonis.model.document;1"
            xmlns="@boc-eu.com/boc-is/adonis.model.document;1"
            xmlns:repoxml="@boc-eu.com/boc-is/adonis.model.document;1"
            xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
            elementFormDefault="qualified">
<xsd:element name="groupStructure">
  <xsd:complexType>
    <xsd:sequence>
      <xsd:element ref="modelgroups" minOccurs="0" maxOccurs="unbounded" />
    </xsd:sequence>
    <xsd:attribute name="date" type="xsd:string"  use="required" />
    <xsd:attribute name="time" type="xsd:string"  use="required" />
    <xsd:attribute name="userid" type="xsd:string"  use="required" />
  </xsd:complexType>
</xsd:element>

<xsd:element name="modelgroups">
  <xsd:complexType>
    <xsd:sequence>
      <xsd:choice maxOccurs="unbounded" >
        <xsd:element ref="model" minOccurs="0" maxOccurs="unbounded" />
        <xsd:element ref="modelgroups" minOccurs="0" maxOccurs="unbounded" />
      </xsd:choice>
    </xsd:sequence>
    <xsd:attribute name="name" type="xsd:string"  use="required" />
    <xsd:attribute name="id" type="xsd:string"  use="required" />
    <xsd:attribute name="grouppermission" type="xsd:string"  use="required" />
  </xsd:complexType>
</xsd:element>

<xsd:element name="model">
  <xsd:complexType>
    <xsd:attribute name="name" type="xsd:string"  use="required" />
    <xsd:attribute name="id" type="xsd:string"  use="required" />
    <xsd:attribute name="modelpermission" type="xsd:string"  use="required" />
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

# note VERIFY_PASSWORD needs the user to have access to the Admin Toolkit
CC "UserMgt" VERIFY_PASSWORD user:("test") password:("test") singlesignon:(0)
CC "Documentation" XML_MODELGROUP_STRUCTURE_OF_USER userid:(userid)
CC "AdoScript" FWRITE file:"c:\\toc.xml" text:(xml) binary:0

{% endraw %}
```
{: .line-numbers}

