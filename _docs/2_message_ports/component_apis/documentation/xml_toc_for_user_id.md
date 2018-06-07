---
layout: commandcall
category: CommandCall
title: "XML_TOC_FOR_USER_ID"
tags: 1.3 1.5
---

XML_TOC_FOR_USER_ID generates an XML file giving the table of contents for the currently logged on user.

# Syntax:  

```adoscript
{% raw %}
CC "Documentation" XML_TOC_FOR_USER_ID update-toc:intValue

#--> RESULT ecode:intValue xml:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`update-toc`|intValue, indicates whether the table of contents should be updated first of all.|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`xml`|strValue, a string containing the resulting XML|

# Remarks:

The variant tag with in the output XML will only hold the variant for loaded models. This message port command will not load every model in order to get the variant of the model; as a consequence the variant will only be filled for previously loaded models.

The used XSD schema is listed below.

# See Also:  



Example 1:

Retrieve the XML representation of the TOC for the current user  
```adoscript
{% raw %}

CC "Documentation" XML_TOC_FOR_USER_ID update-toc:(1)
CC "AdoScript" FWRITE file:"d:\\temp\\toc.xml" text:(xml) binary:0

{% endraw %}
```
{: .line-numbers}

XSL schema:

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
      <xsd:element ref="library" minOccurs="1" maxOccurs="1" />
      <xsd:element ref="toc" minOccurs="0" maxOccurs="unbounded" />
    </xsd:sequence>
  </xsd:complexType>
</xsd:element>

<xsd:element name="library">
  <xsd:complexType>
    <xsd:attribute name="name" type="xsd:string"  use="required" />
    <xsd:attribute name="type" type="xsd:string"  use="required" />
    <xsd:attribute name="version" type="xsd:string"  use="required" />
    <xsd:attribute name="context" type="xsd:string"  use="required" />
  </xsd:complexType>
</xsd:element>


<xsd:complexType name="root2Type">
  <xsd:sequence>
    <xsd:element ref="group" minOccurs="0" maxOccurs="unbounded" />
  </xsd:sequence>
</xsd:complexType>

<xsd:element name="toc">
  <xsd:complexType>
    <xsd:sequence>
	<xsd:element name="root" type="root2Type" minOccurs="0" maxOccurs="unbounded" />
    </xsd:sequence>
  </xsd:complexType>
</xsd:element>


<xsd:element name="group">
  <xsd:complexType>
    <xsd:sequence>
      <xsd:choice maxOccurs="unbounded" >
        <xsd:element ref="group" minOccurs="0" maxOccurs="unbounded" />
        <xsd:element ref="model" minOccurs="0" maxOccurs="unbounded" />
      </xsd:choice>
    </xsd:sequence>
    <xsd:attribute name="id" type="xsd:string"  use="required" />
    <xsd:attribute name="name" type="xsd:string"  use="required" />
  </xsd:complexType>
</xsd:element>

<xsd:element name="model">
  <xsd:complexType>
    <xsd:attribute name="name" type="xsd:string"  use="required" />
    <xsd:attribute name="id" type="xsd:string"  use="required" />
    <xsd:attribute name="variantid" type="xsd:string"  use="required" />
    <xsd:attribute name="class" type="xsd:string"  use="required" />
    <xsd:attribute name="version" type="xsd:string"  use="required" />
    <xsd:attribute name="idclass" type="xsd:string"  use="required" />
  </xsd:complexType>
</xsd:element>


</xsd:schema>
{% endraw %}
```
{: .line-numbers}

