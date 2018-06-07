---
layout: commandcall
category: CommandCall
title: "SET_CONNECTOR_MARKS"
tags: 1.3 1.5
---

SET_CONNECTOR_MARKS turns the creation of connector marks on or off.

# Syntax:  

```adoscript
{% raw %}
CC "Modeling" SET_CONNECTOR_MARKS	[ id | modelid:id ] [ create:boolValue ] .


# --> RESULT ecode:intValue .

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`id`|modifier|
|`modelid`|id|
|`create`|boolValue|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|


# Remarks:

This command is useful where it shall be guaranteed that printing is performed with (resp. without) connector marks. By now there is no corresponding read command, but the reading the connector marks status can therefore be done via the connector marks model attribute.

# See Also:  



Example 1:

```adoscript
{% raw %}

# setting the creation of connector marks of the active model
CC "Modeling" SET_CONNECTOR_MARKS create    # "on"
CC "Modeling" SET_CONNECTOR_MARKS create:0  # "off"
CC "Modeling" SET_CONNECTOR_MARKS create:1  # "on"

{% endraw %}
```
{: .line-numbers}


