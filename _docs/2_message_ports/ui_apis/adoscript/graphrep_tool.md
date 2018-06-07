---
layout: commandcall
category: CommandCall
title: "GRAPHREP_TOOL"
tags: 1.3 1.5
---

This command shows a dockable window (=tool) which displays one or more GraphReps.

# Syntax:

```adoscript
{% raw %}
CC "AdoScript" GRAPHREP_TOOL	graphrep:strValue[ title:strValue] [ interval:intValue]
								[ align:strValue] [ index:intValue] [ subindex:intValue]
								[ min-w:intValue] [ min-h:intValue]
								[hide-close-button] [not-movable]

# --> RESULT ecode:intValue .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`graphrep`|strValue, the GraphRep(s) to be displayed. If several are given, each part has again to start with the keyword "GRAPHREP".|
|`title`|strValue, the title of the dockable window|
|`interval`|intValue, time in milliseconds to switch between several given GraphReps. Default is 10000, i.e. 10 seconds. When the last of several GraphReps was displayed, again the first is shown (endless loop).|
|`align`|strValue, specifies where the window is shown. Possible values are "top", "left", "right" and "bottom". Default is "left".|
|`index`|intValue, defines the index of the workpanel (starting with 0, i.e. top/left). Default is 0.|
|`subindex`|intValue, gives the index of the tool within the workpanel (starting with 0). Default is 4711.|
|`min-w`|intValue, the minimum width of the tool in pixel. Moving/sizing other tool windows should respect that minimum size.|
|`min-h`|intValue, the minimum height of the tool in pixel. Moving/sizing other tool windows should respect that minimum size.|
|`hide-close-button`|modifier, specifies if close button should be hidden. If so, the tool window can not be closed. It will also remain, if F11 is pressed to enter fullscreen mode.|
|`not-movable`|modifier, specifies if the tool window should not be movable. If so, the tool window will only change its position indirectly by moving/sizing other tool windows.|

# Returns:  

|`ecode`|intValue, contains the error code or 0 if no error occured|

# Remarks:

The dockable window framework in ADOxx allows to have windows on four sides: top, left, right, bottom.  
At each side a sequence of "workpanels" can exist. Each workpanel can contain one or several tool panels, which actually contain the single tools.  
In the standard ADOxx configuration the tool "Quickaccess" is located at the top, the tools "Explorer" and "Navigator" are located in one workpanel on the left and the modelling bar is also located at the left side, but in a different workpanel.  
The query and simulation result as well as the message window is located at the bottom part of the application window.

The default values of the parameters "align", "index" and "subindex" create a tool window in the bottomleft area of the window. As it is aligned left, having something displayed in the bottom part will mean that the tool is moved upwards a little.

Within the graphrep a HOTSPOT element with an associated script can be defined. When the hotspot is clicked, the given script is executed.

Note that while it is possible to set only min-w (or min-h) and not both, the platform actually only supports the cases that both restrictions are given or both are not given!

Note the correct masking of " and \ characters when defining complex GraphReps within the command, see also the example below!

# See Also:



Example 1:

```adoscript
{% raw %}

CC "AdoScript" GRAPHREP_TOOL title:"News in the Community" 
								hide-close-button not-movable 
								min-w:350 min-h:300 
								graphrep:"GRAPHREP 
											SET filename:\"c:\\\\pdp.bmp\" 
											SHADOW off 
											FILL color:$88dd22 
											RECTANGLE x:0 y:0 w:(w) h:(h) 
											BITMAPINFO (filename) 
											BITMAP (filename) x:1cm y:1cm 
														w:(bmpwidth / 96 ** 2.54cm) 
														h:(bmpheight / 96 ** 2.54cm)
											TEXT \"Below is an image which is not scaled\"
											HOTSPOT script:\"EXECUTE file:\\\"c:\\\\\\\\test.asc\\\" \" 
																	x:1cm y:1cm 
																	w:(bmpwidth / 96 ** 2.54cm) 
																	h:(bmpheight / 96 ** 2.54cm)"
{% endraw %}
```
{: .line-numbers}

