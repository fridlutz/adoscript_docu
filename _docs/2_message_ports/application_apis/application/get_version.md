---
layout: commandcall
category: CommandCall
title: "GET_VERSION"
tags: 1.3 1.5
---

!!! Check if allowed to be public or not !!!  
GET_VERSION returns information about the current version of the ADOxx or ADOxx-based application.

# Syntax:  

```adoscript
{% raw %}
CC "Application" GET_VERSION	

#--> RESULT version:strValue patch:strValue buildstr:strValue 
			verid:intValue verhigh:intValue verlow:intValue 
			ul:intValue hf:intValue build:intValue
			productname:strValue toolkit:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

none

# Returns:  

|`version`|strValue|
|`patch`|strValue|
|`buildstr`|strValue|
|`verid`|intValue|
|`verhigh`|intValue|
|`verlow`|intValue|
|`ul`|intValue|
|`hf`|intValue|
|`build`|intValue|
|`productname`|strValue, contains the name of the application (e.g. UML@ADOxx).|
|`toolkit`|strValue, contains the toolkit name (e.g. "UML@ADOxx Modelling Toolkit").|


# Remarks:

The most useful return variable is patch, which has the same format in any ADOxx-based toolkit version and allows to check for compatibility.

# See Also:  



Example 1:

Get current version of the ADOxx-based Tool.  
```adoscript
{% raw %}

CC "Application" GET_VERSION

{% endraw %}
```
{: .line-numbers}
