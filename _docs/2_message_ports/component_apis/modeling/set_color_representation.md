---
layout: commandcall
category: CommandCall
title: "SET_COLOR_REPRESENTATION"
tags: 1.3 1.5
---

SET_COLOR_REPRESENTATION sets color conversion methods for all GraphRep drawings.

# Syntax:  

```adoscript
{% raw %}
CC "Modeling" SET_COLOR_REPRESENTATION [ pen:ColorRepMode ] [ fill:ColorRepMode ]
									   [ font:ColorRepMode ] .


ColorRepMode :	"color" | "grayscale" | 
"grayscale-dark" | "grayscale-light" |
	"black" | "white".



# --> RESULT ecode:intValue .

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`pen`|ColorRepMode|
|`fill`|ColorRepMode|
|`font`|ColorRepMode|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|


# Remarks:

With pen, the color conversion methods for GraphRep's PEN elements is specified, while fill is the same for FILL and font is the same for FONT.  
At program start, color representation mode "color" is active for PEN, FILL and FONT, which means that colors are used as defined. Any other color representation mode uses a transformation method before the color is applied.

Color Representation Modes  
"color"	No color conversion.  
"grayscale"	Conversion to grayscale color.  
"grayscale-dark"	Conversion to grayscale color and additional shading.  
"grayscale-light"	Conversion to grayscale color and additional lightening.  
"black"	Any color is replaced with black.  
"white"	Any color is replaced with white.

Where no mode is specified, the current color conversion method is left unchanged.

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Modeling" SET_COLOR_REPRESENTATION pen:"grayscale" fill:"grayscale"
CC "Modeling" SET_COLOR_REPRESENTATION
        pen:"grayscale-dark" fill:"grayscale-light"
CC "Modeling" SET_COLOR_REPRESENTATION pen:"black" fill:"white"

{% endraw %}
```
{: .line-numbers}

![](/images/SET_COLOR_REPRESENTATION.png)
