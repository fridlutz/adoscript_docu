---
layout: commandcall
category: CommandCall
title: "GET_CUSTOMER_NUMBER"
tags: 1.3 1.5
---

The command GET_CUSTOMER_NUMBER returns the customer number.

# Syntax:  

```adoscript
{% raw %}
CC "Application" GET_CUSTOMER_NUMBER 

#--> RESULT ecode:intValue customernumber:strValue 
{% endraw %}
```
{: .line-numbers}

# Parameters:  

none

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`customernumber`|strValue, the value of the customer number.|

# Remarks:



# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Application" debug GET_CUSTOMER_NUMBER 

{% endraw %}
```
{: .line-numbers}


