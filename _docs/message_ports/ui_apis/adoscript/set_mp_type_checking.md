---
layout: commandcall
category: CommandCall
title: "SET_MP_TYPE_CHECKING"
tags: 1.3 1.5
---

SET_MP_TYPE_CHECKING turns the type checking of commands in adoscript messageports on or off.

# Syntax:  

```adoscript
{% raw %}
CC "AdoScript" SET_MP_TYPE_CHECKING ( on | off ) .
{% endraw %}
```
{: .line-numbers}
# Parameters:  

|`on`|modifier|
|`off`|modifier|

# Returns:  

none

# Remarks:

By default (at startup of the application), type checking is turned off (for reasons of compatibility). Though it is strongly recommended always to switch the type checking on once directly after the initialization of the application, because otherwise parameter errors in adoscript are hard to find.

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "AdoScript" INFOBOX "Provoke an aleo-36 error by calling INFOBOX without passing an argument"
CC "AdoScript" SET_MP_TYPE_CHECKING on
CC "AdoScript" INFOBOX

CC "AdoScript" INFOBOX "Do it again, this time without type checking"
CC "AdoScript" SET_MP_TYPE_CHECKING off
CC "AdoScript" INFOBOX

CC "AdoScript" INFOBOX "Done."

{% endraw %}
```
{: .line-numbers}
The third command in the example provokes the following error message. The sixth command is also invalid but as type checking is turned off, no error message will be displayed.

Example 2:

```adoscript
{% raw %}

ON_EVENT "AppInitialized"
{
   CC "AdoScript" SET_MP_TYPE_CHECKING on
}

{% endraw %}
```
{: .line-numbers}
Insert SET_MP_TYPE_CHECKING into the "AppInitialized" event handler (see ).

