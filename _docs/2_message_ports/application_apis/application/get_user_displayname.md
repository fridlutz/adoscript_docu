---
layout: commandcall
category: CommandCall
title: "GET_USER_DISPLAYNAME"
tags: 1.3 1.5
---

The command GET_USER_DISPLAYNAME returns the displayname of the current user.

# Syntax:  

```adoscript
{% raw %}
CC "Application" GET_USER_DISPLAYNAME

#--> RESULT user:strValue 
{% endraw %}
```
{: .line-numbers}

# Parameters:  

none

# Returns:  

|`user`|strValue|

# Remarks:

The difference to GET_USER is that in SSO (Single Sign On) mode the displayname (like "user1") is returned instead of the GUID string.

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Application" debug GET_USER_DISPLAYNAME

{% endraw %}
```
{: .line-numbers}


