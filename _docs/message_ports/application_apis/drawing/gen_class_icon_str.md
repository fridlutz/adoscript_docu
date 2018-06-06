---
layout: commandcall
category: CommandCall
title: "GEN_CLASS_ICON_STR"
tags: 1.3 1.5
---

GEN_CLASS_ICON_STR generates a class icon graphics to a base64 encoded string.

# Syntax:  

```adoscript
{% raw %}
CC "Drawing" GEN_CLASS_ICON_STR	classid:intValue gfx-format:ImageType w:intValue h:intValue
								[ scale:realValue ] [ bgcolor:ColorSpec ] [ transparent ]
								[ bpp:intValue ] [ quality:intValue ]  .

ImageType :		"bmp" | "gif" | "ico" | "jpeg" | "png" |
				"targa" | "tiff" | "wbmp" | "xpm" .

ColorSpec :		ColorValue | ColorName .

ColorValue :	intValue | "ColorName" .
{% endraw %}
```
{: .line-numbers}
Here is the list of predefined ADOxx &lt;color names&gt; .

```adoscript
{% raw %}
# --> RESULT ecode:intValue gfx:strValue 
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`classid`|intValue, the ID of the class of which the icon graphics shall be generated|
|`gfx-format`|strValue, specifies the used image format (see the list below).|
|`w`|intValue, the width of the generated image in pixels|
|`h`|intValue, the height of the generated image in pixels|
|`scale`|realValue, The scale factor is used for drawing class symbols. If it is too large for fitting the image size it is reduced automatically. The default for scale is 1.0. The ADOxx modeling toolbar uses 0.33. Specifying scale for relation class icons has no effect.|
|`bgcolor`|ColorSpec, the background color. It is ignored when bpp is 32, as this means that the background will be transparent.|
|`transparent`|modifier; If gfx-format is "gif" and transparent is true, the background color palette entry is used as transparency indicator. For other formats transparent is ignored.|
|`bpp`|intValue, sets the number of bits per pixel.|
|`quality`|intValue, only applies for jpeg graphics and specifies the compression rate. A value of 100 (percent) means lossless graphics with large files. The default value is 50.|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`gfx`|strValue, contains the generated graphics as base64 encoded string.|

# Remarks:

The supported bpp values depend on the used graphics format (see the list below). For graphics formats which support just one bpp value, the value of this parameter is ignored. If an unsupported bpp value is given, the default bpp value of the specified gfx format is used, which is 8 for GIF, 1 for WBMP and 24 for any other gfx format.

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

[color names](color_names.html "color names")  


Example 1:

```adoscript
{% raw %}

CC "Core" GET_CLASS_ID classname:"Activity"
CC "Drawing" GEN_CLASS_ICON_STR classid:(classid)
								w:35 h:16 
								gfx-format:"png" bpp:32
								
CC "AdoScript" FWRITE file:"d:\\Activity.png" text:(gfx) base64

{% endraw %}
```
{: .line-numbers}

Example 2:

```adoscript
{% raw %}

CC "Core" GET_CLASS_ID classname:"Activity"
CC "Drawing" GEN_CLASS_ICON_STR classid:(classid)
								w:90 h:50 
								gfx-format:"gif" 
								bgcolor:pink 
								transparent
CC "AdoScript" FWRITE file:"d:\\Activity.gif" text:(gfx) base64

{% endraw %}
```
{: .line-numbers}
For transparent GIFs a backround color should be used which does not exist in the class symbol. Using bgcolor:pink should mostly be an appropriate solution.  
