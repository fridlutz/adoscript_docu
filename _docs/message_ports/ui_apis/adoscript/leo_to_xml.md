---
layout: commandcall
category: CommandCall
title: "LEO_TO_XML"
tags: 1.3 1.5
---

LEO_TO_XML converts a LEO text to an XML text. This makes it possible to parse a LEO text with an XML parser.

# Syntax:  

```adoscript
{% raw %}
CC "AdoScript" LEO_TO_XML strValue [ with-header:boolValue ] [ roottag:strValue ]

# --> RESULT xml:strValue ecode:intValue .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`<main_parameter> `|strValue, the LEO text to be converted to XML format|
|`with-header`|boolValue|
|`roottag`|strValue ]|

# Returns:  

|`xml`|strValue|
|`ecode`|intValue|

# Remarks:



# See Also:  



Example 1 (Conversion of an AttrRep definition):

```adoscript
{% raw %}

CC "Core" GET_CLASS_ID classname:"Ende"
CC "Core" GET_ATTR_ID classid:(classid) attrname:"GraphRep"
CC "Core" GET_ATTR_VAL objid:(classid) attrid:(attrid)

CC "AdoScript" LEO_TO_XML (val) with-header roottag:"leoxml"

CC "AdoScript" VIEWBOX text:(val + "\n---------------------\n\n" + xml)
GRAPHREP
SHADOW off

AVAL sp:"Sprache"
IF (sp = "System") {
    SET sp:(cond(_uilang = "de", "Deutsch", "Englisch"))
}
AVAL t:"Typ"
AVAL i:"Reihenfolge"
AVAL d:"Darstellung"
AVAL col:"fontcolor"
AVAL set-default:"nein" mono:"Monochrome Darstellung"
SET bMono:(mono = "ja")

IF (bMono) {
  FILL color:white
  PEN w:0.05cm
} ELSE {
  FILL color:yellow
  SHADOW off
  CLIP_ELLIPSE rx:.7cm ry:.7cm
  GRADIENT_RECT x:-.7cm y:-.7cm w:1.4cm h:1.4cm style:downdiag color1:$ffff66 color2:$eeee00
  CLIP_OFF
  PEN w:0.08cm color:$888800
  FILL style:null
}

ELLIPSE rx:.7cm ry:.7cm
PEN

IF (t = "global") {
  FILL style:null
  ELLIPSE rx:.6cm ry:.6cm
}
IF (d = "mit Namen") {
  FONT color:(col)
  IF (sp = "Deutsch") {
    ATTR "Name" y:.8cm w:c:1.00cm h:t
  } ELSE {
    ATTR "Name (english)" y:.8cm w:c:1.00cm h:t
  }
}
IF (i > "0") {
  FONT "Arial" h:10.0pt bold color:black
  ATTR "Reihenfolge" x:0.00cm y:0.00cm w:c:1.00cm h:c
}

{% endraw %}
```
{: .line-numbers}

The resulting XML is  
```adoscript
{% raw %}
<?xml version="1.0" encoding="UTF-8"?>
<leoxml>
<graphrep />
<shadow opt-off="true" />
<aval val-sp="Sprache" />
<if val="((sp)=(&quot;System&quot;))">
    <set val-sp="(cond((_uilang)=(&quot;de&quot;),&quot;Deutsch&quot;,&quot;Englisch&quot;))" />
</if>
<aval val-t="Typ" />
<aval val-i="Reihenfolge" />
<aval val-d="Darstellung" />
<aval val-col="fontcolor" />
<aval val-set-default="nein" val-mono="Monochrome Darstellung" />
<set val-bMono="((mono)=(&quot;ja&quot;))" />
<if val="(bMono)">
    <fill modifier-color="white" />
    <pen val-w=".05cm" />
</if>
<else>
    <fill modifier-color="yellow" />
    <shadow opt-off="true" />
    <clip-ellipse val-rx=".7cm" val-ry=".7cm" />
    <gradient-rect val-x="-.7cm" val-y="-.7cm" val-w="1.4cm" val-h="1.4cm" modifier-style="downdiag" val-color1="16777062" val-color2="15658496" />
    <clip-off />
    <pen val-w=".08cm" val-color="8947712" />
    <fill modifier-style="null" />
</else>
<ellipse val-rx=".7cm" val-ry=".7cm" />
<pen />
<if val="((t)=(&quot;global&quot;))">
    <fill modifier-style="null" />
    <ellipse val-rx=".6cm" val-ry=".6cm" />
</if>
<if val="((d)=(&quot;mit Namen&quot;))">
    <font val-color="(col)" />
    <if val="((sp)=(&quot;Deutsch&quot;))">
        <attr val="Name" val-y=".8cm" modifier-w="c" val-w="1cm" modifier-h="t" />
    </if>
    <else>
        <attr val="Name (english)" val-y=".8cm" modifier-w="c" val-w="1cm" modifier-h="t" />
    </else>
</if>
<if val="((i)>(&quot;0&quot;))">
    <font val="Arial" opt-bold="true" val-h=".35cm" modifier-color="black" />
    <attr val="Reihenfolge" val-x="0cm" val-y="0cm" modifier-w="c" val-w="1cm" modifier-h="c" />
</if>
</leoxml>

{% endraw %}
```
{: .line-numbers}

