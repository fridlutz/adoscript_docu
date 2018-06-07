---
layout: commandcall
category: CommandCall
title: "EXEC_GFX_DLG"
tags: 1.3 1.5
---

EXEC_GFX_DLG shows the dialog for generating graphics of a model.

# Syntax:  

```adoscript
{% raw %}
CC "Modeling" EXEC_GFX_DLG [ id | modelid:id ]
						   [ mode:Mode ] 
						   [ RegionParams | PagesParams ]
						   [ destination:Destination ] 
						   [ FileParams ] 
						   [ auto-execute ] .


Mode :	"region" | "pages" .


RegionParams :	[ scale:intValue ] .


PagesParams :	[ layout:strValue ] [ orientation:OrientationValue ]
[ factor:intValue | fitonepage |
  pages-height:intValue | pages-width:intValue ]
[ dpi:intValue ] .


OrientationValue :	"portrait" | "landscape" .


Destination :	"file" | "clipboard" .


FileParams :	filename:strValue gfx-format:GfxFormat .


GfxFormat :	"bmp1" | "bmp24" | "bmp" | "pcx8" | "pcx24" | "pcx" |
	"jpg" | "png" | "emf" | "svg" .


# --> RESULT ecode:intValue .

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`id`|modifier|
|`modelid`|id|
|`mode`|Mode|
|`scale`|intValue|
|`layout`|strValue|
|`orientation`|OrientationValue|
|`factor`|intValue|
|`fitonepage`|modifier|
|`pages-height`|intValue|
|`pages-width`|intValue|
|`dpi`|intValue|
|`destination`|Destination|
|`filename`|strValue|
|`gfx-format`|GfxFormat|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|


# Remarks:

The ID of the model of which gfx shall be generated is passed via modelid. If no modelid is specified, the currently active model is being attached.  
With the flag auto-execute being specified, the graphics is being generated without showing the dialog, just as if the user would click on the OK button immediately.  
The destination of a gfx generation can be a file or the system's clipboard. For destination:"file" the name (filename) and the format (gfx-format) of the file can be specified.  
With mode:"region" the gfx is generated for the current gfx region. If no gfx region is active in the model window, the whole drawing area is used. The size of the gfx can be influenced via the scale parameter, where 100 means original size (100%), which is also the default value.  
With mode:"pages" one gfx file is generated for each page of the drawing area. Therefore the filename must contain "XXYY" which is replaced by the page coordinates for each generated page gfx. The size of a page is defined by the used page layout, which can be specified with layout and orientation. If no layout is specified, the current page layout of the model is used. The parameters factor, fitonepage, pages-height or pages-width define the scaling mode. The size of the gfx is determined by the page size, the scaling mode and the dpi value.

Gfx formats  
"bmp1"	Windows Bitmap (monochrome)  
"bmp24"	Windows Bitmap (24 bit)  
"bmp"	Windows Bitmap (24 bit)  
"pcx8"	ZSoft PC-Paintbrush (8bit palette)  
"pcx24"	ZSoft PC-Paintbrush (24 bit)  
"pcx"	ZSoft PC-Paintbrush (24 bit)  
"jpg"	JPEG graphics format  
"png"	Portable Network Graphics  
"emf"	Windows Enhanced MetaFile  
"svg"	Scalable Vector Graphics


# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Modeling" EXEC_GFX_DLG mode:"region" scale:50
    destination:"file" filename:"c:\\ei.png" gfx-format:"png"

{% endraw %}
```
{: .line-numbers}


Example 2:

```adoscript
{% raw %}

CC "Modeling" EXEC_GFX_DLG mode:"pages"
    layout:"Full page" orientation:"landscape" factor:100 dpi:72
    destination:"file" filename:"c:\\eiXXYY.png" gfx-format:"png"

{% endraw %}
```
{: .line-numbers}

