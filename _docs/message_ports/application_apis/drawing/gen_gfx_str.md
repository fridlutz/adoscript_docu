---
layout: commandcall
category: CommandCall
title: "GEN_GFX_STR"
tags: 1.3 1.5
---

GEN_GFX_STR generates graphics of a model to a base64 encoded string. In oposite to the similar command of the "Modeling" message port, this one works without having a model window opened.

# Syntax:  

```adoscript
{% raw %}
CC "Drawing" GEN_GFX_STR modelid:id gfx-format:ImageType 
						[ scale:doubleValue ] [ bpp:intValue ] 
						[ quality:intValue ]  .

ImageType :		"bmp" | "gif" | "ico" | "jpeg" | "png" |
				"targa" | "tiff" | "wbmp" | "xpm"  |  "svg".

# --> RESULT ecode:intValue gfx:strValue w:intValue h:intValue 
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|id, he ID of the model of which gfx shall be generated.|
|`gfx-format`|strValue, specifies the used image format (see table below).|
|`scale`|doubleValue, determines the size of the generated image. The value specifies the scale factor. It's default value is 1.0, which means "original size" (= zoom factor 100%).|
|`bpp`|intValue, sets the number of bits per pixel.|
|`quality`|intValue|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`gfx`|strValue|
|`w`|intValue, the width of the generated image in pixels|
|`h`|intValue, the height of the generated image in pixels|

# Remarks:  
In case of "svg", the returned gfx value is an svg string similar to what is generated into a file when using the message port command GENERATE_GFX and destination:"file".

The bpp value The supported bpp values depend on the used graphics format (see table below). For graphics formats which support just one bpp value, the value of this parameter is ignored. If an unsupported bpp value is given, the default bpp value of the specified gfx format is used, which is 8 for GIF, 1 for WBMP and 24 for any other gfx format.

Gfx formats and supported bpp values

"bmp" - Windows Bitmap (1, 4, 8, 16, 24, 32)  
"gif" - Graphics Interchange Format (8)  
"ico" - Windows Icon (1, 4, 8, 16, 24, 32)  
"jpeg" - JPEG graphics format (8, 24)  
"png" - Portable Network Graphics (1, 4, 8, 24, 32)  
"targa" - Truevision Targa (8, 16, 24, 32)  
"tiff" - Tagged Image File Format (1, 4, 8, 24, 32)  
"wbmp" - Wireless Bitmap (1)  
"xpm" - X11 Pixmap (24)  
"svg" - SVG


# See Also:  



Example:

