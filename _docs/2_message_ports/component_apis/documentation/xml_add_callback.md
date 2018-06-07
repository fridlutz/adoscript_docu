---
layout: commandcall
category: CommandCall
title: "XML_ADD_CALLBACK"
tags: 1.3 1.5
---

XML_ADD_CALLBACK registers a callback procedure for the XML parser.

# Syntax:  

```adoscript
{% raw %}
CC "Documentation" XML_ADD_CALLBACK	strValue name:strValue [ type:strValue ]

#--> RESULT ecode:intValue .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`<main_parameter>`|strValue, name of the procedure that should be called when parsing the element. The procedure has to be defined with XML_SET_SCRIPT first.|
|`name`|strValue, the name of the xml element for which the procedure should be called. Only one procedure per element can be registered. One procedure may be invoked an an element "**": this procedure will be invoked on all elements for that no other callback handler has been installed.|
|`type`|strValue, set either to elementstart (default) or to elementend. Defines if the procedure should be called when the start-element is parsed (e.g. &lt;MODEL&gt;) or when the end-element is parsed (&lt;/MODEL&gt;). Using type, for one element, two procedures may be registered: one for the elementstart and one for the elementend.|

# Returns:  

ecode - intValue, contains the error code or is 0 in case of success; Some error codes: 3 - XML_NOPARSER - a file has to be opened first; 5 - XML_INVALIDCALLBACKTYPE - the argument "type" has not been set to a valid value; 8 - XML_MISSINGATTRIBUTE - either the elementname or the procedure has not been specified; 9 - XML_MISSINGPROCEDURE - the specified procedure is not defined in the AdoScript set with XML_SET_SCRIPT; 10 - XML_PROCEDUREALREADYDEFINED - for the specified element, a procedure has already been defined.

# Remarks:



# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Documentation" XML_SET_SCRIPT raw {
    PROCEDURE CREATEMODEL name:string id:int {
        CC "AdoScript" INFOBOX
                ("Invoked the procedure on node " + name
                 + " with id " + id)
    }

    PROCEDURE DEFAULT {
        # invoked on all nodes but the "MODEL" nodes
    }
}

CC "Documentation" XML_ADD_CALLBACK "CREATEMODEL" name:"MODEL" type:"elementstart"
CC "Documentation" XML_ADD_CALLBACK "DEFAULT" name:"**" type:"elementstart"

{% endraw %}
```
{: .line-numbers}

