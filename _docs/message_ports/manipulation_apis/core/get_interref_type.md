---
layout: commandcall
category: CommandCall
title: "GET_INTERREF_TYPE"
tags: 1.3 1.5
---

GET_INTERREF_TYPE returns the parameter type, which is "model" if the attribute specified in attrid contains model references, or "instance" if the attribute contains references to modeling instances.

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_INTERREF_TYPE attrid:id .


#-->RESULT ecode:intValue type:Type
{% endraw %}
```
{: .line-numbers}

```adoscript
{% raw %}
Type :	"model" | "instance" .

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`attrid`|id|

# Returns:  

|`ecode`|intValue, contains the error code or is 0 in case of success.|
|`type`|Type|

# Remarks:



# See Also:  



Example:

