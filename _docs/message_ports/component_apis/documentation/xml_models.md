---
layout: commandcall
category: CommandCall
title: "XML_MODELS"
tags: 1.3 1.5
---

XML_MODELS generates an XML file containing the models or model groups with or with out attribute profiles or profile groups.

# Syntax:  

```adoscript
{% raw %}
CC "Documentation" XML_MODELS 	modelids:strValue mgroupids:strValue
								attrprofs:strValue apgroups:strValue
								[ NoRecordRows ]

NoRecordRows :	no-record-rows[: 1|0] |
				no-record-rows:attributes:strValue .

#--> RESULT ecode:intValue xml:strValue .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelids`|strValue, a space separated list of model IDs.|
|`mgroupids`|strValue, a space separated list of model group ids.|
Either a list of model ids or a list of model group Ids has to be given to the XML_MODELS command.
|`attrprofs`|strValue, can be either left out or set to 1, to indicate that all referenced attribute profiles in the requested model/model group list should be included with in the xml output.|
|`apgroups`|strValue, a space separated list of attribute profile group ids. It takes precedence over the withattrprofile flag (if a list of attribute profile group ids are given then only the attribute profiles in the requested attribute profile groups will be included in the xml output.|
|`no-record-rows`|if specified, record rows are not exported. This may be used for performance enhancement, when record contents are not needed momentarily. Alternatively you can specify a list of record attribute IDs, for which no rows are exported. The content of a single records can be exported with XML_RECORD.|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`xml`|strValue, contains the resulting xml string.|

# Remarks:

The used XSD schema is listed below.

# See Also:  



Example 1:

Retrieve xml description of model of a list of modelids  
```adoscript
{% raw %}

CC "Documentation" XML_MODELS modelids:(modelids) mgroupids:("") attrprofs:("") apgroups:("") 
CC "AdoScript" FWRITE file:"d:\\temp\\modelidsout.xml" text:(xml) binary:0

{% endraw %}
```
{: .line-numbers}

Example 2:

Retrieve xml description of model of a list of model group IDs  
```adoscript
{% raw %}

CC "Documentation" XML_MODELS modelids:("") mgroupids:(mgroupids) attrprofs:("") apgroups:(" ") 
CC "AdoScript" FWRITE file:"d:\\temp\\modelgroupsout.xml" text:(xml) binary:0

{% endraw %}
```
{: .line-numbers}

Example 3:

Retrieve xml description of model and attributes of a list of model group ids and attribute Ids  
```adoscript
{% raw %}

CC "Documentation" XML_MODELS modelids:("") mgroupids:(mgroupids) attrprofs:("") apgroups:( apgroups) 
CC "AdoScript" FWRITE file:"d:\\temp\\modelgroupsandattrout.xml" text:(xml) binary:0

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
<xsd:element name="adoxml">
  <xsd:complexType>
    <xsd:sequence>
      <xsd:element ref="attrprofdir" minOccurs="0" maxOccurs="unbounded" />
      <xsd:element ref="attributeprofiles" minOccurs="0" maxOccurs="unbounded" />
      <xsd:element ref="models" minOccurs="0" maxOccurs="unbounded" />
      <xsd:element ref="modelgroups" minOccurs="0" maxOccurs="unbounded" />
    </xsd:sequence>
    <xsd:attribute name="version" type="xsd:string"  use="required" />
    <xsd:attribute name="date" type="xsd:string"  use="required" />
    <xsd:attribute name="time" type="xsd:string"  use="required" />
    <xsd:attribute name="database" type="xsd:string"  use="required" />
    <xsd:attribute name="username" type="xsd:string"  use="required" />
    <xsd:attribute name="adoversion" type="xsd:string"  use="required" />
  </xsd:complexType>
</xsd:element>

<xsd:element name="attributeprofiles">
  <xsd:complexType>
    <xsd:sequence>
      <xsd:element ref="attributeprofile" minOccurs="0" maxOccurs="unbounded" />
    </xsd:sequence>
  </xsd:complexType>
</xsd:element>

<xsd:element name="attrprofdir">
  <xsd:complexType>
    <xsd:sequence>
      <xsd:element ref="attributeprofile" minOccurs="0" maxOccurs="unbounded" />
      <xsd:element ref="attrprofdir" minOccurs="0" maxOccurs="unbounded" />
      <xsd:element ref="interref" minOccurs="0" maxOccurs="unbounded" />
    </xsd:sequence>
    <xsd:attribute name="name" type="xsd:string"  use="required" />
  </xsd:complexType>
</xsd:element>

<xsd:element name="attributeprofile">
  <xsd:complexType>
    <xsd:sequence>
      <xsd:choice maxOccurs="unbounded" >
        <xsd:element ref="attribute" minOccurs="0" maxOccurs="unbounded" />
        <xsd:element ref="record" minOccurs="0" maxOccurs="unbounded" />
        <xsd:element ref="interref" minOccurs="0" maxOccurs="unbounded" />
      </xsd:choice>
    </xsd:sequence>
    <xsd:attribute name="class" type="xsd:string"  use="required" />
    <xsd:attribute name="name" type="xsd:string"  use="required" />
    <xsd:attribute name="version" type="xsd:string"  use="required" />
    <xsd:attribute name="applib" type="xsd:string"  use="required" />
  </xsd:complexType>
</xsd:element>

<xsd:element name="models">
  <xsd:complexType>
    <xsd:sequence>
      <xsd:element ref="model" minOccurs="0" maxOccurs="unbounded" />
    </xsd:sequence>
  </xsd:complexType>
</xsd:element>

<xsd:element name="model">
  <xsd:complexType>
    <xsd:sequence>
      <xsd:element ref="modelattributes" minOccurs="0" maxOccurs="unbounded" />
      <xsd:element ref="instance" minOccurs="0" maxOccurs="unbounded" />
      <xsd:element ref="connector" minOccurs="0" maxOccurs="unbounded" />
    </xsd:sequence>
    <xsd:attribute name="id" type="xsd:string"  use="required" />
    <xsd:attribute name="name" type="xsd:string"  use="required" />
    <xsd:attribute name="version" type="xsd:string"  use="required" />
    <xsd:attribute name="modeltype" type="xsd:string"  use="required" />
    <xsd:attribute name="libtype" type="xsd:string"  use="required" />
    <xsd:attribute name="applib" type="xsd:string"  use="required" />
  </xsd:complexType>
</xsd:element>

<xsd:element name="modelgroups">
  <xsd:complexType>
    <xsd:sequence>
      <xsd:element ref="modelgroup" minOccurs="0" maxOccurs="unbounded" />
    </xsd:sequence>
  </xsd:complexType>
</xsd:element>

<xsd:element name="modelgroup">
  <xsd:complexType>
    <xsd:sequence>
      <xsd:element ref="modelreference" minOccurs="0" maxOccurs="unbounded" />
      <xsd:element ref="modelgroup" minOccurs="0" maxOccurs="unbounded" />
    </xsd:sequence>
    <xsd:attribute name="name" type="xsd:string"  use="required" />
  </xsd:complexType>
</xsd:element>

<xsd:element name="modelreference">
  <xsd:complexType>
    <xsd:sequence>
      <xsd:element ref="modelattributes" minOccurs="0" maxOccurs="unbounded" />
      <xsd:element ref="instance" minOccurs="0" maxOccurs="unbounded" />
      <xsd:element ref="connector" minOccurs="0" maxOccurs="unbounded" />
    </xsd:sequence>
    <xsd:attribute name="name" type="xsd:string"  use="required" />
    <xsd:attribute name="version" type="xsd:string"  use="required" />
    <xsd:attribute name="modeltype" type="xsd:string"  use="required" />
    <xsd:attribute name="libtype" type="xsd:string"  use="required" />
  </xsd:complexType>
</xsd:element>

<xsd:element name="modelattributes">
  <xsd:complexType>
    <xsd:sequence>
      <xsd:choice maxOccurs="unbounded" >
        <xsd:element ref="attribute" minOccurs="0" maxOccurs="unbounded" />
        <xsd:element ref="record" minOccurs="0" maxOccurs="unbounded" />
        <xsd:element ref="interref" minOccurs="0" maxOccurs="unbounded" />
      </xsd:choice>
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

<xsd:element name="instance">
  <xsd:complexType>
    <xsd:sequence>
      <xsd:choice maxOccurs="unbounded" >
        <xsd:element ref="attribute" minOccurs="0" maxOccurs="unbounded" />
        <xsd:element ref="record" minOccurs="0" maxOccurs="unbounded" />
        <xsd:element ref="interref" minOccurs="0" maxOccurs="unbounded" />
      </xsd:choice>
    </xsd:sequence>
    <xsd:attribute name="id" type="xsd:string" use="required" />
    <xsd:attribute name="class" type="xsd:string"  use="required" />
    <xsd:attribute name="name" type="xsd:string"  use="required" />
  </xsd:complexType>
</xsd:element>

<xsd:element name="connector">
  <xsd:complexType>
    <xsd:sequence>
      <xsd:element ref="from" minOccurs="1" maxOccurs="1" />
      <xsd:element ref="to" minOccurs="1" maxOccurs="1" />
      <xsd:choice maxOccurs="unbounded" >
        <xsd:element ref="attribute" minOccurs="0" maxOccurs="unbounded" />
        <xsd:element ref="record" minOccurs="0" maxOccurs="unbounded" />
        <xsd:element ref="interref" minOccurs="0" maxOccurs="unbounded" />
      </xsd:choice>
    </xsd:sequence>
    <xsd:attribute name="id" type="xsd:string" use="required" />
    <xsd:attribute name="class" type="xsd:string"  use="required" />
  </xsd:complexType>
</xsd:element>

<xsd:element name="from">
  <xsd:complexType>
    <xsd:attribute name="instance" type="xsd:string" use="required" />
    <xsd:attribute name="class" type="xsd:string" use="required" />
  </xsd:complexType>
</xsd:element>

<xsd:element name="to">
  <xsd:complexType>
    <xsd:attribute name="instance" type="xsd:string" use="required" />
    <xsd:attribute name="class" type="xsd:string" use="required" />
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
