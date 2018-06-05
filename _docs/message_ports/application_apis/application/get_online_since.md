---
layout: commandcall
category: CommandCall
title: "GET_ONLINE_SINCE"
tags: 1.3 1.5
---

The command GET_ONLINE_SINCE returns the date and time since you are online.

# Syntax:  

```adoscript
{% raw %}
CC "Application" GET_ONLINE_SINCE [date-format:strValue] [time-format:strValue]

#--> RESULT date:strValue 
			time:strValue 
{% endraw %}
```
{: .line-numbers}

# Parameters:  

date-format - strValue, DD (01-31), DDD (Mon-Sun), MM (01-12), MMM (Jan-Dec), YY (00-99), YYYY (1900 - 2999)
|`time-format`|strValue, HH (00-23), MM (00-59), SS (00-59)|

# Returns:  

|`date`|strValue|
|`time`|strValue|

# Remarks:

If the format string is not defined, then the Windows language style is used.

Do not use the Windows language style for logfiles. You will get different formats from different computers.

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Application" debug GET_ONLINE_SINCE date-format:"DD.MM.YYYY" time-format:"HH:MM:SS"
CC "Application" debug GET_ONLINE_SINCE date-format:"ddd, dd. mmm yyyy"

{% endraw %}
```
{: .line-numbers}


