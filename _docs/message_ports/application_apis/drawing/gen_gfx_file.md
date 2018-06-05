---
layout: commandcall
category: CommandCall
title: "GEN_GFX_FILE (Drawing)"
tags: 1.3 1.5
---

GEN_GFX_FILE generates graphics of a model to a file without instantiating user interface classes (like percentage window). In oposite to the similar command of the "Modeling" message port, this one works without having a model window opened.

# Syntax:  

```adoscript
{% raw %}
CC "Drawing" GEN_GFX_FILE	modelid:intValue filename:strValue gfx-format:ImageType
							[ scale:realValue ] [ bpp:intValue ] [ quality:intValue ]

ImageType :		"bmp" | "gif" | "ico" | "jpeg" | "png" |
				"targa" | "tiff" | "wbmp" | "xpm" 

# --> RESULT ecode:intValue w:intValue h:intValue 
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|intValue, the ID of the model of which gfx shall be generated.|
|`filename`|strValue, the name of the destination file.|
|`gfx-format`|strValue, specifies the used image format (see the list below).|
|`scale`|realValue, determines the size of the generated image. The value specifies the scale factor. It's default value is 1.0, which means "original size" (= zoom factor 100%).|
|`bpp`|intValue, sets the number of bits per pixel.|
|`quality`|intValue, only applies for jpeg graphics and specifies the compression rate. A value of 100 (percent) means lossless graphics with large files. The default value is 50.|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`w`|intValue, the width of the generated image in pixels|
|`h`|intValue, the height of the generated image in pixels|

# Remarks:

The supported bpp values depend on the used graphics format (see table below). For graphics formats which support just one bpp value, the value of this parameter is ignored. If an unsupported bpp value is given, the default bpp value of the specified gfx format is used, which is 8 for GIF, 1 for WBMP and 24 for any other gfx format.

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

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Drawing" GEN_GFX_FILE modelid:(modelid) scale:1.0
    filename:"c:\\ei.png" gfx-format:"png"

{% endraw %}
```
{: .line-numbers}

