---
layout: commandcall
category: CommandCall
title: "GET_ALL_MODELTYPES"
tags: 1.3 1.5
---

The command GET_ALL_MODELTYPES retrieves the names of all modeltypes.

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_ALL_MODELTYPES [libtype:["bp"|"we"]] [sep:strValue]

#--> RESULT ecode:intValue modeltypes:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`libtype`|strValue, used for determining whether modeltypes of the ADOxx Dynamic Library (bp) or ADOxx Static Library (we) should be retrieved. If missing, all the modeltypes will be retrieved.|
|`sep`|strValue, specifies the separator with which the resulting strings should be separated. Default is a single whitespace (" ").|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success|
|`modeltypes`|strValue, list of modeltype names separated by the separator defined with "sep"|

# Remarks:



# See Also:  



Example 1:

```adoscript
{% raw %}

# get all BP modeltypes
CC "Core" GET_ALL_MODELTYPES libtype:"bp"
SET bpmt:(modeltypes)

# get all WE modeltypes
CC "Core" GET_ALL_MODELTYPES libtype:"we"
SET wemt:(modeltypes)

CC "Core" GET_ALL_MODELTYPES
SET mt:(modeltypes)

CC "AdoScript" INFOBOX ("BP modeltypes: " + (bpmt) + "\nWE modeltypes: " + (wemt) + "\nAll modeltypes: " + (mt))

{% endraw %}
```
{: .line-numbers}

- get all BP modeltypes  
- get all WE modeltypes  
- get all modeltypes  
- print 'em

