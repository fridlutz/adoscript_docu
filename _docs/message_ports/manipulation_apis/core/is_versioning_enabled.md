---
layout: commandcall
category: CommandCall
title: "IS_VERSIONING_ENABLED"
tags: 1.3 1.5
---

IS_VERSIONING_ENABLED checks whether or not the time based versioning is enabled in the current library.

# Syntax:  

```adoscript
{% raw %}
CC "Core" IS_VERSIONING_ENABLED

#--> RESULT ecode:intValue versioning: 1|0
{% endraw %}
```
{: .line-numbers}

# Parameters:  

none

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`versioning`|1|0, is set to 1 if time based versioning is enabled, and 0 otherwise.|


# Remarks:



# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Core" IS_VERSIONING_ENABLED
SET s:"You are NOT working with a library with time based versioning"
IF (versioning) {
   SET s:(replall(s, "NOT ", ""))
}
CC "AdoScript" INFOBOX (s)

{% endraw %}
```
{: .line-numbers}

