---
layout: commandcall
category: CommandCall
title: "GEN_MODELTYPE_ICON_STR"
tags: 1.3 1.5
---

GEN_MODELTYPE_ICON_STR generates a model type icon graphics to a base64 encoded string.

# Syntax:  

```adoscript
{% raw %}
CC "Drawing" GEN_MODELTYPE_ICON_STR	modeltype:strValue [ gfx-format:ImageType ]
									[ bgcolor:ColorSpec ] [ transparent ]
									[ bpp:intValue ] [ quality:intValue ]
									[ modified[:boolValue] ]
									[ favorite[:boolValue] ]
									[ protected[:boolValue] ]
									[ cycle[:boolValue] ]
									[ locked[:boolValue] ]
									[ unlocked[:boolValue] ]

ImageType :	"bmp" | "gif" | "ico" | "jpeg" | "png" |
			"targa" | "tiff" | "wbmp" | "xpm" .


ColorSpec :		ColorValue | ColorName .

ColorValue :	intValue | "ColorName" .
{% endraw %}
```
{: .line-numbers}
Here is the list of predefined ADOxx &lt;color names&gt; .

```adoscript
{% raw %}
# --> RESULT ecode:intValue gfx:strValue .

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modeltype`|strValue, the name of the model type of which the icon graphics shall be generated.|
|`gfx-format`|strValue, specifies the used image format (see table below). Default is "png".|
|`bgcolor`|ColorSpec, the background color. This is ignored when bpp is 32, as this means that the background will be transparent.|
|`transparent`|modifier|
|`bpp`|intValue, value sets the number of bits per pixel.|
|`quality`|intValue, only applies for jpeg graphics and specifies the compression rate. A value of 100 (percent) means lossless graphics with lage files. The default value is 50.|
|`modified`|boolValue, red coloring for showing "modified" status|
|`favorite`|boolValue, yellow star at the top right-hand side|
|`protected`|boolValue, lock at the bottom right-hand side|
|`cycle`|boolValue, blue arrow at the top right side|
|`locked`|boolValue, forbidden sign|
|`unlocked`|boolValue, check mark|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`gfx`|strValue, contains the generated graphics as base64 encoded string.|

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

If gfx-format is "gif" and transparent is true, the background color palette entry is used as transparency indicator. For other formats transparent is ignored.

# See Also:  

[color names](color_names.html "color names")  


Example 1:

```adoscript
{% raw %}

CC "Drawing" GEN_MODELTYPE_ICON_STR
        modeltype:"Business process" gfx-format:"png" bpp:32
CC "AdoScript" FWRITE file:"d:\\BP.png" text:(gfx) base64

{% endraw %}
```
{: .line-numbers}

Example 2:

```adoscript
{% raw %}

CC "Drawing" GEN_MODELTYPE_ICON_STR
        modeltype:"Business process" gfx-format:"gif"
        bgcolor:pink transparent
CC "AdoScript" FWRITE file:"d:\\BP.gif" text:(gfx) base64

{% endraw %}
```
{: .line-numbers}

