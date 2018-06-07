---
layout: commandcall
category: CommandCall
title: "SET_ACTIVE_VARIANT (Modeling)"
tags: 1.3 1.5
---

SET_ACTIVE_VARIANT switches to a variant the same way as when selecting the corresponding menu item. If a layout algorithm is associated with the new variant that layout algorithm is executed in some cases (see below).

# Syntax:  

```adoscript
{% raw %}
CC "Modeling" SET_ACTIVE_VARIANT	[ modelid:modelId ] variant:strValue
									[ missing-positions:MissingPositions ]
									[ no-layalg-execution:boolValue ]
									[ layout-algorithm:strValue ]
									[ quiet:boolValue ] .


MissingPositions :	"ask" | "from-old-variant" | "auto" .

{% endraw %}
```
{: .line-numbers}

```adoscript
{% raw %}
# --> RESULT ecode:intValue .

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|modelId|
|`variant`|strValue|
|`missing-positions`|MissingPositions|
|`no-layalg-execution`|boolValue|
|`layout-algorithm`|strValue|
|`quiet`|boolValue|

# Returns:  

|`ecode`|intValue, the return variable ecode is set to 0 if the command call was successful, to 1 otherwise.|


# Remarks:

The model whose variant shall be activated can be specified with modelid. Default is the current active model. The name of the variant which shall be activated has to be specified with variant.

With missing-positions the treatment of objects without positions in the new variant can be set. If "ask" or nothing is specified, the user is aked which method shall be applied. If "from-old-variant" is specified, the positions for objects without position are taken from the old (previous active) variant. If "auto" is specified, these objects are moved to free places in the drawing area.

If no-layalg-execution is passed without value or with value 1, no layout algorithm is executed after the variant has been set. Otherwise, if all objects in the new variant do not have positions yet and exactly one layout algorithm is associated with the new variant, the associated layout algorithm is executed. If more than one layout algorithm is associated with the new variant, the preferred one must be specified with layout-algorithm. Otherwise no layout algorithm is executed.

If quiet is passed without value or with value 1, additional UI messages (like "no swimlanes have been generated" etc.) are not shown. However, this command might still show UI messages, e.g. if missing-positions:"ask" is passed.



# See Also:  



Example 1:

```adoscript
{% raw %}

# always without layout algorithm execution
CC "Modeling" SET_ACTIVE_VARIANT
        variant:"Without swimlanes (horizontal)"
        missing-positions:"from-old-variant"
        no-layalg-execution quiet
# eventually with layout algorithm execution
CC "Modeling" SET_ACTIVE_VARIANT
        variant:"With swimlanes (vertical)"
        missing-positions:"from-old-variant"
        layout-algorithm:"With swimlanes (vertical)"
        quiet

{% endraw %}
```
{: .line-numbers}


