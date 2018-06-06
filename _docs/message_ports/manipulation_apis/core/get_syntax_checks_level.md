---
layout: commandcall
category: CommandCall
title: "GET_SYNTAX_CHECKS_LEVEL"
tags: 1.3 1.5
---

GET_SYNTAX_CHECKS_LEVEL returns the syntax checks level of the current library.

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_SYNTAX_CHECKS_LEVEL

#--> RESULT ecode:intValue lever: strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

none

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`level`|strValue|

# Remarks:

The syntax checks level is initialized at loading of an application library according to the value of library attribute "Default settings". In addition to that static setting, a dynamic change of the syntax checks level is possible with SET_SYNTAX_CHECKS_LEVEL.

For temporary changing the syntax checks level you should read the current value with GET_SYNTAX_CHECKS_LEVEL, so it can later be set to the original value again.

# See Also:  

[SET_SYNTAX_CHECKS_LEVEL](set_syntax_checks_level.html "SET_SYNTAX_CHECKS_LEVEL")  


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

