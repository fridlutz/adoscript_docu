---
layout: commandcall
category: CommandCall
title: "GET_MODEL_GROUP_TREE_XML"
tags: 1.3 1.5
---

GET_MODEL_GROUP_TREE_XML generates an XML string containing the current model group tree structure.

# Syntax:  

```adoscript
{% raw %}
CC "Documentation" GET_MODEL_GROUP_TREE_XML	[ with-access-modes[: 1|0] ]
											[ with-user-group-names[: 1|0] ]
											[ with-variant-ids[: 1|0] ]
											[ with-end-comment[: 1|0] ] 

#--> RESULT ecode:intValue xml:strValue .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`with-access-modes`|by default, for all model groups the related user group access modes are written as subtags of the model group tags. When access mode information is not needed, set with-access-modes to 0 or false.|
|`with-user-group-names`|by default, user groups are written as user group IDs. If with-user-group-names is specified, additionally the name and the "is system user" flag of user groups are written.|
|`with-variant-ids`|if the with-variant-ids flag is set (default: false), for all models a variant attribute is contained in the related model tags. However, the active variant is only put out for loaded models.|
|`with-end-comment`|if the with-end-comment flag is set (default: false), a comment is appended at the end of the XML text, which states the number of model groups and the number of models.|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`xml`|strValue, the resulting XML string|

# Remarks:

The XML structure is defined by the following XSD schema  
```adoscript
{% raw %}
<?xml version="1.0" encoding="UTF-8"?>

<!-- XML schema for CC "Documentation" GET_MODEL_GROUP_TREE. -->
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"
            targetNamespace="@boc-eu.com/boc-is/adonis.model.document;1"
            xmlns="@boc-eu.com/boc-is/adonis.model.document;1"
            xmlns:repoxml="@boc-eu.com/boc-is/adonis.model.document;1"
            xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
            elementFormDefault="qualified">

<xsd:element name="root">
  <xsd:complexType>
    <xsd:sequence>
      <xsd:element ref="group" minOccurs="0" maxOccurs="unbounded" />
    </xsd:sequence>
  </xsd:complexType>
</xsd:element>

<xsd:element name="group">
  <xsd:complexType>
    <xsd:sequence>
      <xsd:choice maxOccurs="unbounded" >
        <xsd:element ref="access" minOccurs="0" maxOccurs="unbounded" />
        <xsd:element ref="group" minOccurs="0" maxOccurs="unbounded" />
        <xsd:element ref="model" minOccurs="0" maxOccurs="unbounded" />
      </xsd:choice>
    </xsd:sequence>
    <xsd:attribute name="id" type="xsd:string"  use="required" />
    <xsd:attribute name="name" type="xsd:string"  use="required" />
  </xsd:complexType>
</xsd:element>

<xsd:element name="access">
  <xsd:complexType>
    <xsd:attribute name="usergroupid" type="xsd:string"  use="required" />
    <xsd:attribute name="usergroup" type="xsd:string"  use="optional" />
    <xsd:attribute name="sys" type="xsd:string"  use="optional" />
    <xsd:attribute name="mode" type="xsd:string"  use="required" />
  </xsd:complexType>
</xsd:element>

<xsd:element name="model">
  <xsd:complexType>
    <xsd:attribute name="id" type="xsd:string"  use="required" />
    <xsd:attribute name="name" type="xsd:string"  use="required" />
    <xsd:attribute name="version" type="xsd:string"  use="required" />
    <xsd:attribute name="class" type="xsd:string"  use="required" />
    <xsd:attribute name="idclass" type="xsd:string"  use="required" />
    <xsd:attribute name="variantid" type="xsd:string"  use="optional" />
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

SET t0:(getTickCount())
CC "Documentation" GET_MODEL_TREE_XML with-end-comment
SET t1:(getTickCount())
CC "AdoScript" INFOBOX ("Time: " + STR ((t1 - t0) ** 0.001) + "s")
CC "AdoScript" VIEWBOX text:(xml)

{% endraw %}
```
{: .line-numbers}

