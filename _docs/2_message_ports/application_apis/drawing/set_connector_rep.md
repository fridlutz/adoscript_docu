---
layout: commandcall
category: CommandCall
title: "SET_CONNECTOR_REP"
tags: 1.3 1.5
---

SET_CONNECTOR_REP sets the representation of connectors for a model.

# Syntax:  

```adoscript
{% raw %}
CC "Drawing" SET_CONNECTOR_REP	modelid:intValue 
								[ rounded: "default" | "always" | "never"] 
								[ bridges: "default" | "always" | "never" ]
								[ cmarks-create:boolValue ]
								[ cmarks-midsection: "hide" | "shadow" | "show" ]
								[ cmarks-position: "bendpoint" | "border" | "all-pages" ]

# --> RESULT ecode:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|intValue, the ID of the model|
rounded - strValue, has the following values: "default"	- Bendpoints will be drawn as specified in GraphRep, "always" - All bendpoints will be drawn with rounded angles, "never" - All bendpoints will be drawn with sharp angles.
bridges - strValue, "default" - Bridges will be drawn as specified in GraphRep, "always" - Bridges will be drawn at all crossings, "never" - Bridger will never be drawn.
|`cmarks-create`|boolValue, 0 = All connectors will be drawn without connector marks, 1 = Connector marks will be drawn at connector-page crossings.|
cmarks-midsection - strValue, "hide" - Sections between connector marks will not be drawn, "shadow" - Sections between connector marks will be drawn as "shadows", "show" - Sections between connector marks will be drawn normally.
cmarks-position - strValue, "bendpoint" - Connector marks will be placed at last bendpoints, "border" - Connector marks will be placed at page borders, "all-pages" - Connector marks will be placed at page borders on all related pages.

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|

# Remarks:

These settings correspond wirh the settings in the "Connector representation" dialog of the modeling component.

As for all commands of the "Drawing" message port, it is not required here to have a model window opened. So the connector representation can be set easily before generationg graphics using CC "Drawing" GEN_GFX_FILE / GEN_GFX_STR.

For optional parameters which are not specified the corresponding value (which is stored in a model attribute) is left unchanged.

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Drawing" SET_CONNECTOR_REP modelid:(modelid)
      rounded:"default" bridges:"always"
      cmarks-create:1 cmarks-midsection:"hide" cmarks-position:"border"

{% endraw %}
```
{: .line-numbers}

