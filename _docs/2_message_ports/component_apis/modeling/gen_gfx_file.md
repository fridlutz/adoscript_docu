---
layout: commandcall
category: CommandCall
title: "GEN_GFX_FILE (Modeling)"
tags: 1.3 1.5
---

GEN_GFX_FILE generates graphics of a model to a file without instantiating user interface classes (like percentage window).

# Syntax:  

```adoscript
{% raw %}
CC "Modeling"
GEN_GFX_FILE	modelid:id filename:strValue gfx-format:ImageType
	[ scale:intValue ] [ bpp:intValue ] [ quality:intValue ] .


ImageType :	"bmp" | "gif" | "ico" | "jpeg" | "png" |
	"targa" | "tiff" | "wbmp" | "xpm" .



-->RESULT ecode:intValue w:intValue h:intValue .

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|id, the ID of the model of which gfx shall be generated is passed via modelid.|
|`filename`|strValue, the name of the destination file is passed via filename.|
|`gfx-format`|ImageType, the gfx-format specifies the used image format (see table below).|
|`scale`|intValue, the scale parameter determines the size of the generated image. The value specifies the zoom factor. It's default value is 100, which means "original size".|
|`bpp`|intValue, the bpp value sets the number of bits per pixel. The supported bpp values depend on the used graphics format (see table below).|
|`quality`|intValue, the quality value just applies for jpeg graphics and specifies the compression rate. A value of 100 (percent) means lossless graphics with lage files. The default value is 50.|

# Returns:  

|`ecode`|intValue, when graphics generation fails ecode has a nonzero value.|
|`w`|intValue, the image width in pixels|
|`h`|intValue, the image height in pixels|

# Remarks:

For graphics formats which support just one bpp value, the value of this parameter is ignored. If an unsupported bpp value is given, the default bpp value of the specified gfx format is used, which is 8 for GIF, 1 for WBMP and 24 for any other gfx format.

Gfx formats and supported bpp values  
"bmp"	Windows Bitmap (1, 4, 8, 16, 24, 32)  
"gif"	Graphics Interchange Format (8)  
"ico"	Windows Icon (1, 4, 8, 16, 24, 32)  
"jpeg"	JPEG graphics format (8, 24)  
"png"	Portable Network Graphics (1, 4, 8, 24, 32)  
"targa"	Truevision Targa (8, 16, 24, 32)  
"tiff"	Tagged Image File Format (1, 4, 8, 24, 32)  
"wbmp"	Wireless Bitmap (1)  
"xpm"	X11 Pixmap (24)

For files of type "ico" the following image size conditions must be true:  
16 ≤ width ≤ 128 and 16 ≤ height ≤ 128.

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Modeling" GEN_GFX_FILE modelid:(modelid) scale:100
    filename:"c:\\ei.png" gfx-format:"png"

{% endraw %}
```
{: .line-numbers}


