---
layout: commandcall
category: CommandCall
title: "GET_VARIANTS_OF_MODELTYPE"
tags: 1.3 1.5
---

GET_VARIANTS_OF_MODELTYPE returns all variant names which are defined for a certain model type.

# Syntax:  

```adoscript
{% raw %}
CC "Drawing" GET_VARIANTS_OF_MODELTYPE	strValue

# --> RESULT ecode:intValue variants:arrayOfStrings
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`<main-parameter>`|strValue, name of model type|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`variants`|arrayOfStrings, contains the names of the variants|

# Remarks:

If no variants are defined for the specified model type, the array is empty (variants.length = 0). Otherwise the first array element, variants[0], is an empty string, which stands for the automatically created variant, which is named "&lt;No variant&gt;" at the UI.

If the variant names are needed as token string this can be constructed, for instance, with tokstr(variants, "\n").  
The return variable ecode is set to 0 if the command call was successful, to 1 otherwise (i.e. an unknown model type name has been passed).

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Core" GET_ALL_MODELTYPES
SET s:""
FOR mt in:(modeltypes) {
    SET s:(s + "Model type \"" + mt + "\":\n")
    CC "Drawing" GET_VARIANTS_OF_MODELTYPE (mt)
    IF (variants.length) {
        FOR v from:0 to:(variants.length - 1) {
            SET s:(s + "    Variant #" + STR v + ": ")
            SET s:(s + "\"" + variants[v] + "\"\n")
        }
    } ELSE {
        SET s:(s + "    (no variants defined)\n")
    }
    SET s:(s + "\n")
}
CC "AdoScript" VIEWBOX text:(s)

{% endraw %}
```
{: .line-numbers}

