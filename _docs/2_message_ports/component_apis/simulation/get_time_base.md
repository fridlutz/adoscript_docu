---
layout: commandcall
category: CommandCall
title: "GET_TIME_BASE"
tags: 1.3 1.5
---

Returns the current time base of the simulation component.  

# Syntax:  

```adoscript
{% raw %}
CC "Simulation" GET_TIME_BASE

#--> RESULT ecode:intValue 
			dpy:days-per-year 
			hpd:hours-per-day
{% endraw %}
```
{: .line-numbers}

# Parameters:  

none

# Returns:  

|`ecode`|intValue, always 0|
|`dpy`|realValue, holds the days per year; E.g. 170.5 days per year|
|`hpd`|realValue, holds the working hours per day; E.g. 7.5 hours per day|

# Remarks:

The time base is used by ADOxx to convert the ADOxx time format (yy:ddd:hh:mm:ss) to seconds and vice versa.

# See Also:

