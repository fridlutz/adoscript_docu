---
layout: commandcall
category: CommandCall
title: "NUMBER_MODEL"
tags: 1.3 1.5
---



# Syntax:  

```adoscript
{% raw %}
    CC "Modeling" NUMBER_MODEL [ modelid:intValue]  
							   [ lefttoright:1|0 ]
							   [ excludedclasses:stringValue ] 
							   [ with-dialog ] 
							   [ silent ]


# --> RESULT ecode:intValue

{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`modelid`|intValue|
|`lefttoright`|1|0|
|`excludedclasses`|stringValue|
|`with-dialog`|modifier|
|`silent`|modifier|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|


# Remarks:

This AdoScript command performs a simple numbering:  
Objects are numbered according to its x resp. y coordinate.

If the input parameter modelid is given this model is numbered, otherwise the active model is numbered.  
The parameter lefttoright is used to specify which of the coordinates (x, y) has the higher priority.  
If it is 1, the x coordinate is used as main numbering criteria. Only if two objects have the same x coordinate, the y coordinate is used.  
If it is 0, the y coordinate is used as main numbering criteria. Only if two objects have the same y coordinate, the x coordinate is used.  
This means that a "toptobottom" ordering is used.  
The default value for lefttoright is 1.  
If with-dialog is given, a dialog is shown with classes that should be included in the numbering.  
If with-dialog is not given, excludedclasses allows to specify which classes will not be included in the numbering.  
(As default, all numberable classes are included).  
A class is numberable if it is customized to be so in the library attribute "Arrangement function"  
(There must be an entry ENUMCLASS "&lt;myclass&gt;" attrib:"&lt;myattr&gt;" in an ENUMPROFILE section).  
If silent is given, no success or error message will be displayed.  
If both silent and with-dialog are given, silent overrules the with-dialog option, i.e. it works as if with-dialog had not been specified.

The returned ecode is 0 if the command has been executed successfully.  If there was an error an ecode of 1 is returned.

# See Also:  



Example 1:

```adoscript
{% raw %}

# simply number the instances of the current model from top to bottom
# without showing any class (de)selection dialog
CC "Modeling" NUMBER_MODEL lefttoright:0

{% endraw %}
```
{: .line-numbers}


