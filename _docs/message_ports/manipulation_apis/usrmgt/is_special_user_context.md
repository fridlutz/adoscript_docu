---
layout: commandcall
category: CommandCall
title: "IS_SPECIAL_USER_CONTEXT"
tags: 1.3 1.5
---

IS_SPECIAL_USER_CONTEXT returns a flag which is true if a special user context is currently active.

# Syntax:  

```adoscript
{% raw %}
CC "UserMgt" GET_CURRENT_USER_CONTEXT 

# --> RESULT val:boolValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

none

# Returns:  

|`val`|boolValue|

# Remarks:

A special user context can be activated with SWITCH_USER_CONTEXT. In a special user context the application behaves (temporarily) as if another user than the login user is the active one.

# See Also:  



Example:


