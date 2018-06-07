---
layout: commandcall
category: CommandCall
title: "EXIT"
tags: 1.3 1.5
---

With EXIT the current AdoScript is terminated.

# Syntax:  

```adoscript
{% raw %}
EXIT [ intValue ]
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`<main_parameter>`|intValue, specifies the exit code returned to the caller of the current AdoScript; default is 0.|

# Returns:  



# Remarks:

Note that AdoScripts can be nested (using files, procedures) and that just the deepest running AdoScript is affected. So, if the AdoScript is the body of a procedure just the procedure body is left and the execution continues with the statement after the call of that procedure. If the AdoScript is contained in a string (which eventually has been read from a file before) and executed with EXECUTE, the execution continues with the statement after the EXECUTE.

With the integer value specified after the keyword an exit code can be returned to the caller of the current AdoScript. If the caller is an EXECUTE statement, the exit code can there be assigned to a variable. The default exit code is 0.

# See Also:

[EXECUTE](execute.html "EXECUTE")  

