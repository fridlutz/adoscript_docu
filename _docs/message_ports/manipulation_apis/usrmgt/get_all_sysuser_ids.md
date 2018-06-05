---
layout: commandcall
category: CommandCall
title: "GET_ALL_SYSUSER_IDS"
tags: 1.3 1.5
---

GET_ALL_SYSUSER_IDS returns the IDs of the ADOxx system users.

# Syntax:  

```adoscript
{% raw %}
CC "UserMgt" GET_ALL_SYSUSER_IDS


#-->RESULT userids:strValue ecode:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

none

# Returns:  

|`ecode`|intValue, 0 (meaning success) or 1 (meaning error).|
|`userids`|strValue, containing the IDs of the ADOxx system users (separator: space).|
ecode

# Remarks:

This command is available within both the ADOxx Development Toolkit and the ADOxx Modelling Toolkit.

# See Also:  



Example:

