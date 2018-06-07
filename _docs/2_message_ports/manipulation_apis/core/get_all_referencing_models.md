---
layout: commandcall
category: CommandCall
title: "GET_ALL_REFERENCING_MODELS"
tags: 1.3 1.5
---

GET_ALL_REFERENCING_MODELS returns all models which are referencing specified models.

# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_ALL_REFERENCING_MODELS modelids:strValue .


#-->RESULT ecode:intValue sourcemodelids:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelids`|strValue|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`sourcemodelids`|strValue|

# Remarks:


GET_ALL_REFERENCING_MODELS returns a list of all model IDs (sourcemodelids) which are referencing the models specified by the parameter modelids.  
This means that sourcemodelids contains all models which at least one INTERREF to at least one of the model specified in modelids.

Both modelids and sourcemodelids are space separated strings with the IDs (e.g. "10001 12345 4711").

# See Also:  



Example:

