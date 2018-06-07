---
layout: commandcall
category: CommandCall
title: "COMPUTE_REGION_IMAGE_MAP"
tags: 1.3 1.5
---

COMPUTE_REGION_IMAGE_MAP computes pixel coordinates which objects would have in a generated graphics.

# Syntax:  

```adoscript
{% raw %}
CC "Drawing" COMPUTE_REGION_IMAGE_MAP modelid:intValue 
									[ scale:intValue]
									[ with-swimlanes ]

# --> RESULT ecode:intValue imgmap:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|intValue, the ID of the model of which an image map shall be computed. The model must be loaded in the core component, but it is not needed to have it opened in a model window.|
|`scale`|intValue|
|`with-swimlanes`|modifier, if given, image map information also for swimlanes (if present in the given model) is generated.|

# Returns:  

|`ecode`|intValue, is 0 if successful or contains the errorcode otherwise|
|`imgmap`|strValue, the resulting XML string|

# Remarks:

The resulting XML string imgmap consists of a MAP root element with attributes  MODELID, MODELNAME and MODELTYPE. The MAP element contains for each object or connector one AREA element with the following syntax :

```adoscript
{% raw %}
<AREA ID="id" TYPE="type" CLASSNAME="classname"
SHAPE="rect" COORDS="x1,y1,x2,y2"
BBX="intValue" BBY="intValue" BBW="intValue" BBH="intValue"
SBBX="intValue" SBBY="intValue" SBBW="intValue" SBBH="intValue"
LAYER="intValue" INDEX="intValue" />
{% endraw %}
```
{: .line-numbers}

ID is the object ID, TYPE is "object" or "connector", the BB and SBB values are the coordinates of the object's bounding box (x, y, width, height). While the BB coordinates specify the bounding box of all GraphRep elements, the SBB coordinates specify the "symbol" bounding box, which means that ATTR elements are not considered here. The COORDS element also specifies the bounding box coordinates, but in one string and with the coordinates of the bottom right corner (x2|y2) instead of a width and a height value. LAYER and INDEX together specify the position in the model editor's z-order (should not be needed in most cases).

For modeling objects (TYPE="object"), an AREA tag contains additionally the values XPOS and YPOS, which specify the object's position.  
Aditionally, AREA elements are generated for visualized attributes of each object or connector. These elements have the following syntax :

```adoscript
{% raw %}
<AREA ID="id" TYPE="attribute"
CLASSNAME="classname" ATTRID="id" ATTRNAME="attrname"
SHAPE="rect" COORDS="x1,y1,x2,y2"
BBX="intValue" BBY="intValue" BBW="intValue" BBH="intValue"
LAYER="intValue" INDEX="intValue" />
{% endraw %}
```
{: .line-numbers}

For HOTSPOT elements, attribute area tags contain an additional item HOTSPOT="yes".  
The order of the AREA elements considers the z order of the model editor. Objects which are on top are placed at the beginning of map, visualized attributes of an object are placed before the object itself.

An older relative of this command exists in the "Modeling" message port, which does not write elements for visible attributes and writes XML without header tag :  
&gt; CC "Modeling" COMPUTE_REGION_IMAGE_MAP

# See Also:  



Example:

