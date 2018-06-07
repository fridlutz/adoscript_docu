---
layout: commandcall
category: CommandCall
title: "XML_RECORD_DOCU"
tags: 1.3 1.5
---

XML_RECORD_DOCU generates an XML file containing the content of a single record.

# Syntax:  

```adoscript
{% raw %}
CC "Documentation" XML_RECORD_DOCU	objid:id attrid:id

#--> RESULT ecode:intValue xml:strValue .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`objid`|intValue, the ID of the object|
|`attrid`|intValue, the ID of the attribute|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`xml`|strValue, a string containing the resulting XML|

# Remarks:

This is usually used for dynamic completion of information delivered by XML_MODEL_DOCU with skipping of records.

The used XSD schema is listed below.

# See Also:  

[XML_RECORD](xml_record.html "XML_RECORD")  


Example:


XSD schema:  
```adoscript
{% raw %}
<?xml version="1.0" encoding="UTF-8"?>
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"
            targetNamespace="@boc-eu.com/boc-is/adonis.model.document;1"
            xmlns="@boc-eu.com/boc-is/adonis.model.document;1"
            xmlns:repoxml="@boc-eu.com/boc-is/adonis.model.document;1"
            xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
            elementFormDefault="qualified">
<xsd:element name="adoxml">
  <xsd:complexType>
    <xsd:sequence>
      <xsd:element ref="record" minOccurs="1" maxOccurs="1" />
    </xsd:sequence>
  </xsd:complexType>
</xsd:element>

<xsd:element name="chapter">
  <xsd:complexType>
    <xsd:sequence>
      <xsd:choice maxOccurs="unbounded" >
        <xsd:element ref="group" minOccurs="0" maxOccurs="unbounded" />
        <xsd:element ref="attribute" minOccurs="0" maxOccurs="unbounded" />
      </xsd:choice>
    </xsd:sequence>
    <xsd:attribute name="name" type="xsd:string"  use="required" />
  </xsd:complexType>
</xsd:element>

<xsd:element name="group">
  <xsd:complexType>
    <xsd:sequence>
      <xsd:element ref="attribute" minOccurs="0" maxOccurs="unbounded" />
    </xsd:sequence>
    <xsd:attribute name="visible" type="xsd:string" use="required" />
    <xsd:attribute name="name" type="xsd:string"  use="required" />
  </xsd:complexType>
</xsd:element>

<xsd:element name="attribute">
  <xsd:complexType>
    <xsd:sequence>
      <xsd:choice maxOccurs="unbounded" >
        <xsd:element ref="chapter" minOccurs="0" maxOccurs="unbounded" />
        <xsd:element ref="values" minOccurs="0" maxOccurs="1"  />
        <xsd:element ref="record" minOccurs="0" maxOccurs="1"  />
        <xsd:element name="value" type="xsd:string" minOccurs="0" maxOccurs="1" />
      </xsd:choice>
    </xsd:sequence>
    <xsd:attribute name="id" type="xsd:string" use="required" />
    <xsd:attribute name="name" type="xsd:string"  use="required" />
    <xsd:attribute name="chapter" type="xsd:string"  use="required" />
    <xsd:attribute name="type" type="xsd:string"  use="required" />
  </xsd:complexType>
</xsd:element>

<xsd:element name="values">
  <xsd:complexType>
    <xsd:sequence>
      <xsd:element ref="value" minOccurs="0" maxOccurs="1" />
    </xsd:sequence>
    <xsd:attribute name="count" type="xsd:string" use="required" />
  </xsd:complexType>
</xsd:element>

<xsd:element name="record">
  <xsd:complexType>
    <xsd:sequence>
      <xsd:element ref="row" minOccurs="0" maxOccurs="unbounded" />
    </xsd:sequence>
    <xsd:attribute name="rowcount" type="xsd:string" use="required" />
    <xsd:attribute name="skippedrows" type="xsd:string" use="required" />
  </xsd:complexType>
</xsd:element>

<xsd:element name="row">
  <xsd:complexType>
    <xsd:sequence>
      <xsd:element ref="attribute" minOccurs="0" maxOccurs="unbounded" />
    </xsd:sequence>
    <xsd:attribute name="id" type="xsd:string" use="required" />
    <xsd:attribute name="number" type="xsd:string" use="required" />
  </xsd:complexType>
</xsd:element>

<xsd:element name="interref">
  <xsd:complexType>
    <xsd:sequence>
      <xsd:element ref="value" minOccurs="1" maxOccurs="1" />
    </xsd:sequence>
    <xsd:attribute name="count" type="xsd:string" use="required" />
  </xsd:complexType>
</xsd:element>

<xsd:element name="value">
  <xsd:complexType>
    <xsd:attribute name="type" type="xsd:string"  use="required" />
    <xsd:attribute name="modelid" type="xsd:string"  use="required" />
    <xsd:attribute name="modelname" type="xsd:string"  use="required" />
    <xsd:attribute name="modelversion" type="xsd:string"  use="required" />
    <xsd:attribute name="modeltype" type="xsd:string"  use="required" />
    <xsd:attribute name="objectid" type="xsd:string"  use="optional" />
    <xsd:attribute name="objectname" type="xsd:string"  use="optional" />
    <xsd:attribute name="objectclass" type="xsd:string"  use="optional" />
  </xsd:complexType>
</xsd:element>

</xsd:schema>

{% endraw %}
```
{: .line-numbers}

