---
layout: commandcall
category: CommandCall
title: "XML_RECORD"
tags: 1.3 1.5
---

XML_RECORD generates an XML file containing the content of a single record.

# Syntax:  

```adoscript
{% raw %}
CC "Documentation" XML_RECORD objid:intValue attrid:intValue

#--> RESULT ecode:intValue xml:strValue 
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

This is usually used for dynamic completion of information delivered by XML_MODELS with skipping of records.

The used XSD schema is listed below.

# See Also:  

[XML_RECORD_DOCU](xml_record_docu.html "XML_RECORD_DOCU")  


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
      <xsd:element ref="record" minOccurs="0" maxOccurs="unbounded" />
    </xsd:sequence>
  </xsd:complexType>
</xsd:element>

<xsd:element name="attribute">
  <xsd:complexType mixed="true">
    <xsd:attribute name="name" type="xsd:string"  use="required" />
    <xsd:attribute name="type" type="xsd:string"  use="required" />
  </xsd:complexType>
</xsd:element>

<xsd:element name="interref">
  <xsd:complexType>
    <xsd:sequence>
      <xsd:element ref="iref" minOccurs="0" maxOccurs="unbounded" />
      <xsd:choice maxOccurs="unbounded" >
        <xsd:element ref="attribute" minOccurs="0" maxOccurs="unbounded" />
        <xsd:element ref="record" minOccurs="0" maxOccurs="unbounded" />
        <xsd:element ref="interref" minOccurs="0" maxOccurs="unbounded" />
      </xsd:choice>
    </xsd:sequence>
    <xsd:attribute name="name" type="xsd:string"  use="required" />
  </xsd:complexType>
</xsd:element>

<xsd:element name="iref">
  <xsd:complexType>
    <xsd:sequence>
      <xsd:element ref="row" minOccurs="0" maxOccurs="unbounded" />
      <xsd:choice maxOccurs="unbounded" >
        <xsd:element ref="attribute" minOccurs="0" maxOccurs="unbounded" />
        <xsd:element ref="record" minOccurs="0" maxOccurs="unbounded" />
        <xsd:element ref="interref" minOccurs="0" maxOccurs="unbounded" />
      </xsd:choice>
    </xsd:sequence>
    <xsd:attribute name="type" type="xsd:string"  use="required" />
    <xsd:attribute name="tmodeltype" type="xsd:string"  use="required" />
    <xsd:attribute name="tmodelname" type="xsd:string"  use="required" />
    <xsd:attribute name="tmodelver" type="xsd:string"  use="required" />
    <xsd:attribute name="tclassname" type="xsd:string"  use="optional" />
    <xsd:attribute name="tobjname" type="xsd:string"  use="optional" />
  </xsd:complexType>
</xsd:element>

<xsd:element name="record">
  <xsd:complexType>
    <xsd:sequence>
      <xsd:element ref="row" minOccurs="0" maxOccurs="unbounded" />
      <xsd:choice maxOccurs="unbounded">
        <xsd:element ref="attribute" minOccurs="0" maxOccurs="unbounded" />
        <xsd:element ref="record" minOccurs="0" maxOccurs="unbounded" />
        <xsd:element ref="interref" minOccurs="0" maxOccurs="unbounded" />
      </xsd:choice>
    </xsd:sequence>
    <xsd:attribute name="name" type="xsd:string" use="required" />
    <xsd:attribute name="rowcount" type="xsd:string" use="required" />
    <xsd:attribute name="skippedrows" type="xsd:string" use="required" />
  </xsd:complexType>
</xsd:element>

<xsd:element name="row">
  <xsd:complexType>
    <xsd:sequence>
      <xsd:choice maxOccurs="unbounded" >
        <xsd:element ref="attribute" minOccurs="0" maxOccurs="unbounded" />
        <xsd:element ref="record" minOccurs="0" maxOccurs="unbounded" />
        <xsd:element ref="interref" minOccurs="0" maxOccurs="unbounded" />
      </xsd:choice>
    </xsd:sequence>
    <xsd:attribute name="id" type="xsd:string" use="required" />
    <xsd:attribute name="number" type="xsd:string" use="required" />
  </xsd:complexType>
</xsd:element>

</xsd:schema>
{% endraw %}
```
{: .line-numbers}
