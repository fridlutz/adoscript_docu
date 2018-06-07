---
layout: commandcall
category: CommandCall
title: "GET_OS_INFO"
tags: 1.3 1.5
---

GET_OS_INFO can be used to determine the operating system on which ADOxx is currently running.

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_OS_INFO	

#--> RESULT os:strValue winver_major:strValue winver_minor:strValue
			winver_platform:intValue winver_csdversion:intValue .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

none

# Returns:  

|`os`|strValue, name of the OS|
|`winver_major`|strValue|
|`winver_minor`|strValue|
|`winver_platform`|intValue|
|`winver_csdversion`|intValue|

# Remarks:



# See Also:  



Example 1:


