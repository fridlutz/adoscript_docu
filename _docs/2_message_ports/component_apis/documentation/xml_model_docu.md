---
layout: commandcall
category: CommandCall
title: "XML_MODEL_DOCU"
tags: 1.3 1.5
---

XML_MODEL_DOCU generates an XML file in the document format for a model.

# Syntax:  

```adoscript
{% raw %}
CC "Documentation" XML_MODEL_DOCU modelid:intValue  ( no-record-rows[:boolValue] |
												no-record-rows:attributes: strValue )

#--> RESULT ecode:intValue xml:strValue .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|intValue, ID of the model for which XML is exported.|
|`no-record-rows`|if specified, record rows are not exported. This may be used for performance enhancement, when record contents are not needed momentarily. Alternatively you can specify a list of record attribute IDs, for which no rows are exported. The content of a single records can be exported with XML_RECORD_DOCU.|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`xml`|strValue, a string containing the resulting XML|

# Remarks:

The used XSD schema is listed below.

# See Also:  



Example 1:

Retrieve the model document in XML format for a model id  
```adoscript
{% raw %}

CC "Documentation" XML_MODEL_DOCU modelid:(modelid) 
CC "AdoScript" FWRITE file:"d:\\temp\\modeldoc.xml" text:(xml) binary:0

{% endraw %}
```
{: .line-numbers}

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
<xsd:element name="root">
  <xsd:complexType>
    <xsd:sequence>
      <xsd:element ref="model" minOccurs="1" maxOccurs="1" />
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

<xsd:element name="notebook">
  <xsd:complexType>
    <xsd:sequence>
      <xsd:element ref="chapter" minOccurs="0" maxOccurs="unbounded" />
    </xsd:sequence>
  </xsd:complexType>
</xsd:element>

<xsd:element name="model">
  <xsd:complexType>
    <xsd:sequence>
      <xsd:choice maxOccurs="unbounded" >
        <xsd:element ref="notebook" minOccurs="1" maxOccurs="1" />
        <xsd:element ref="object" minOccurs="1" maxOccurs="unbounded" />
        <xsd:element ref="relation" minOccurs="1" maxOccurs="unbounded" />
      </xsd:choice>
    </xsd:sequence>
    <xsd:attribute name="library" type="xsd:string"  use="required" />
    <xsd:attribute name="id" type="xsd:string"  use="required" />
    <xsd:attribute name="name" type="xsd:string"  use="required" />
    <xsd:attribute name="version" type="xsd:string"  use="required" />
    <xsd:attribute name="type" type="xsd:string"  use="required" />
    <xsd:attribute name="context" type="xsd:string"  use="required" />
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

<xsd:element name="object">
  <xsd:complexType>
    <xsd:sequence>
      <xsd:element ref="notebook" minOccurs="1" maxOccurs="1" />
    </xsd:sequence>
    <xsd:attribute name="id" type="xsd:string" use="required" />
    <xsd:attribute name="name" type="xsd:string"  use="required" />
        <xsd:attribute name="class" type="xsd:string"  use="required" />
    <xsd:attribute name="idclass" type="xsd:string"  use="required" />
  </xsd:complexType>
</xsd:element>

<xsd:element name="relation">
  <xsd:complexType>
    <xsd:sequence>
      <xsd:choice maxOccurs="unbounded" >
        <xsd:element ref="from" minOccurs="1" maxOccurs="1" />
        <xsd:element ref="to" minOccurs="1" maxOccurs="1" />
        <xsd:element ref="notebook" minOccurs="1" maxOccurs="1" />
      </xsd:choice>
    </xsd:sequence>
    <xsd:attribute name="id" type="xsd:string" use="required" />
    <xsd:attribute name="class" type="xsd:string"  use="required" />
    <xsd:attribute name="idclass" type="xsd:string"  use="required" />
  </xsd:complexType>
</xsd:element>

<xsd:element name="from">
  <xsd:complexType>
    <xsd:attribute name="object" type="xsd:string" use="required" />
    <xsd:attribute name="class" type="xsd:string" use="required" />
    <xsd:attribute name="idclass" type="xsd:string" use="required" />
  </xsd:complexType>
</xsd:element>

<xsd:element name="to">
  <xsd:complexType>
    <xsd:attribute name="object" type="xsd:string" use="required" />
    <xsd:attribute name="class" type="xsd:string" use="required" />
    <xsd:attribute name="idclass" type="xsd:string" use="required" />
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

