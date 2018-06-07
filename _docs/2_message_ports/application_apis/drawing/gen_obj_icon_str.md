---
layout: commandcall
category: CommandCall
title: "GEN_OBJ_ICON_STR"
tags: 1.3 1.5
---

GEN_OBJ_ICON_STR generates an icon graphics of a certain graphical object to a base64 encoded string. This is similar to GEN_CLASS_ICON_STR. However, GEN_OBJ_ICON_STR considers object specific graphical representation.

# Syntax:  

```adoscript
{% raw %}
CC "Drawing" GEN_OBJ_ICON_STR	objid:intValue gfx-format:ImageType w:intValue h:intValue
								[ scale:realValue ] [ bgcolor:ColorSpec ] [ transparent ]
								[ bpp:intValue ] [ quality:intValue ]
								[ with-vis-attrs[:boolValue] ]  [ direction:Direction ]

ImageType :		"bmp" | "gif" | "ico" | "jpeg" | "png" |
				"targa" | "tiff" | "wbmp" | "xpm" .

Direction :		left-to-right | top-to-bottom |
				right-to-left | bottom-to-top .


ColorSpec :		ColorValue | ColorName .

ColorValue :	intValue | "ColorName" .

# --> RESULT ecode:intValue gfx:strValue .

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`objid`|intValue, the ID of the object of which the icon graphics shall be generated|
|`gfx-format`|strValue, specifies the used image format (see the list below).|
|`w`|intValue, the width of the generated image in pixels|
|`h`|intValue, the height of the generated image in pixels|
|`scale`|realValue, is used for drawing class symbols. If it is too large for fitting the image size it is reduced automatically. The default for scale is 1.0. The ADOxx modeling toolbar uses 0.33. Specifying scale for relation class icons has no effect.|
|`bgcolor`|ColorSpec, the background color. It is ignored when bpp is 32, as this means that the background will be transparent.|
|`transparent`|modifier; If gfx-format is "gif" and transparent is true, the background color palette entry is used as transparency indicator. For other formats transparent is ignored.|
|`bpp`|intValue, sets the number of bits per pixel.|
|`quality`|intValue, only applies for jpeg graphics and specifies the compression rate. A value of 100 (percent) means lossless graphics with large files. The default value is 50.|
|`with-vis-attrs`|boolValue, if specified without argument or with true value, texts of visualized attributes are drawn into the icon graphics. By default, object icons are generated without visualized attributes.|
|`direction`|Direction|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`gfx`|strValue, contains the generated graphics as base64 encoded string.|

# Remarks:

The scale factor

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

For sizeable objects the current size is considered. For connectors icons are always generated without bendpoints and with centered middle point. The default connector direction is left-to-right. This can be changed via the option direction.

# See Also:  

[GEN_CLASS_ICON_STR](gen_class_icon_str.html "GEN_CLASS_ICON_STR")  
[color names](color_names.html "color names")  


Example 1:

```adoscript
{% raw %}

CC "Modeling" GET_ACT_MODEL
CC "Modeling" GET_SELECTED modelid:(modelid)
SET objid:(VAL objids)
CC "Drawing" GEN_OBJ_ICON_STR objid:(objid)
       w:35 h:16 gfx-format:"png" bpp:32
CC "AdoScript" FWRITE file:"d:\\Activity.png" text:(gfx) base64

{% endraw %}
```
{: .line-numbers}

