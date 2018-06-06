---
layout: commandcall
category: CommandCall
title: "LEO"
tags: 1.3 1.5
---

With LEO a LEOgram can be parsed which is given as string value. This is usefull where an external call delivers structured data in LEO format.

# Syntax:  

```adoscript
{% raw %}
LEO [ parse:stringExpr ] { accessCmd } .

accessCmd :	get-elem-count:varName |
			set-cur-elem-index:intExpr |
			get-keyword:varName |
			is-contained:varName [ :strExpr ] |
			get-str-value:varName [ :strExpr ] |
			get-int-value:varName [ :strExpr ] |
			get-real-value:varName [ :strExpr ] |
			get-tmm-value:varName [ :strExpr ] |
			get-time-value:varName [ :strExpr ] |
			get-modifier:varName:strExpr |
			get-value:varName[:strExpr] .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`parse`|stringExpr, the string containing the LEOgram. If a LEO command has already called before and the parser shall continue with the same LEO text, parse does not have to be specified again.|
|`get-elem-count`|varName, the number of elements can be assigned to a variable.|
|`set-cur-elem-index`|intExpr, a current element can be set (element numbers run from 0 to n-1).|
|`get-keyword`|varName, get the element's keyword|
|`is-contained`|varName, check if an attribute is specified.|
|`get-str-value`|varName, get an attribute value of type string|
|`get-int-value`|varName, get an attribute value of type integer|
|`get-real-value`|varName, get an attribute value of type real|
|`get-tmm-value`|varName, get an attribute value of type measure (cm, pt)|
|`get-time-value`|varName, get an attribute value of type time|
|`get-modifier`|varName, get the modifier of an attribute.|
|`get-value`|varName, get an attribute value of any type. If no attribute name (= strExpr) is specified with get-value the element's own value is taken.|

# Returns:  



# Remarks:



# See Also:  



Example 1:

The following AdoScript decrypts a given LEO text and displays its elements in two subsequent Infoboxes.  
```adoscript
{% raw %}

# A simple LEO text
SET leotext:"PERSON firstname:\"Sun-Tsu\" lastname:\"Liao\"   age:25
             PERSON firstname:\"Victor\"  lastname:\"Davion\" age:30"

# Parse the LEO text the first time to get the number of elements in it
LEO parse:(leotext) get-elem-count:elemcount

# Go through each element in the LEO text
FOR curelem from:0 to:(elemcount - 1) {
    # Access the information of the current element
    LEO set-cur-elem-index:(curelem)
        get-str-value:fname:"firstname" 
        get-str-value:lname:"lastname"
        get-int-value:age:"age"
    CC "AdoScript" INFOBOX (fname + " " + lname + " " + STR age)
}

{% endraw %}
```
{: .line-numbers}



