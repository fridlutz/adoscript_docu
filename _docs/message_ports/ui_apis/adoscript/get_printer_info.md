---
layout: commandcall
category: CommandCall
title: "GET_PRINTER_INFO"
tags: 1.3 1.5
---

GET_PRINTER_INFO returns the name and some other information about the currently active printer.

# Syntax:  

```adoscript
{% raw %}
CC "AdoScript" GET_PRINTER_INFO	[ no-auto-create ]

# --> RESULT ecode:intValue name:strValue
             device:strValue port:strValue 
			 driver:strValue valid:boolValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`no-auto-create`|modifier|

# Returns:  

|`ecode`|intValue, 0 if no errors or 1 if there is no printer installed|
|`name`|strValue, Printer name|
|`device`|strValue, Device name|
|`port`|strValue, Port name|
|`driver`|strValue, Driver name|
|`valid`|boolValue, 0 if the printer cannot be accessed (is currently not available) or 1 if the printer can be accessed|

# Remarks:

When no printer has been used so far (in the current session), the default printer will be accessed automatically. This can be avoided by specifying no-auto-create. With that option, a nonzero ecode will be returned when no printer has been used so far.

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "AdoScript" debug GET_PRINTER_INFO

{% endraw %}
```
{: .line-numbers}

