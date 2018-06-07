---
layout: commandcall
category: CommandCall
title: "SET_SYNTAX_CHECKS_LEVEL"
tags: 1.3 1.5
---

SET_SYNTAX_CHECKS_LEVEL changes the syntax checks level of the current library.

# Syntax:  

```adoscript
{% raw %}
CC "Core" SET_SYNTAX_CHECKS_LEVEL strValue

#-->RESULT ecode:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

none

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|

# Remarks:

The syntax checks level is initialized at loading of an application library according to the value of library attribute "Default settings". In addition to that static setting, a dynamic change of the syntax checks level is possible with this command.

Executing this command does not change the library. The syntax checks level is changed just for the running session.

For temporary changing the syntax checks level you should read the current value with GET_SYNTAX_CHECKS_LEVEL, so it can later be set to the original value again.

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Core" GET_SYNTAX_CHECKS_LEVEL
SET oldSyntaxChecksLevel:(level)
CC "Core" SET_SYNTAX_CHECKS_LEVEL "4.01.02"
// ... (do something)
CC "Core" SET_SYNTAX_CHECKS_LEVEL (oldSyntaxChecksLevel)

{% endraw %}
```
{: .line-numbers}

