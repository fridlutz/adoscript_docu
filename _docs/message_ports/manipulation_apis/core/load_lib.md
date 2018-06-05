---
layout: commandcall
category: CommandCall
title: "LOAD_LIB"
tags: 1.3 1.5
---

LOAD_LIB loads an application library.

# Syntax:  

```adoscript
{% raw %}
CC "Core" LOAD_LIB libid:intValue [ write-protected:intValue ]

#-->RESULT ecode:intValue applibid:intValue bplibid:intValue welibid:intValue .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`libid`|intValue, ID of the library|
|`write-protected`|intValue, you can specify that the library is not going to be changed, but just loaded for reading purposes. However, a library loaded with active "write protected" flag can still be modified. The only difference is that it is not possible that a library is loaded by two users without "write protected" flag at a time.|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`applibid`|intValue, id of the ADOxx Application library|
|`bplibid`|intValue, id of the ADOxx Dynamic library|
|`welibid`|intValue, id of the ADOxx Static library|

# Remarks:

Note that an application library can only be loaded if no other application library is currently loaded. Otherwise the current library has to be discarded explicitely using the DISCARD_LIB command.

This command is only available in the **ADOxx Development Toolkit**.

# See Also:  



Example 1:

```adoscript
{% raw %}

# show all available applicataion libraries
SET sLibs: ""
SET sAvailLibs: ""
CC "Core" GET_ALL_APPLIBS
FOR id in:(applibids) {
    CC "Core" GET_LIB_NAME libid:(VAL id)
    CC "Core" GET_LIB_ID libname:(libname)
    SET sLibs:(sLibs + STR libid + ":\t" + libname + "\n")
    SET sAvailLibs:(sAvailLibs + libname + ";")
}
CC "AdoScript" INFOBOX (sLibs) title:"GET_ALL_LIBS"

# show the current application library
SET applibid: -1
SET applib: ""
CC "Core" GET_CURRENT_LIBS
CC "AdoScript" INFOBOX ("Current application library:\n" + applib) title:"GET_CURRENT_LIBS"

# discard the current library
IF (applibid > 0) {
    CC "Core" DISCARD_LIB
    CC "AdoScript" INFOBOX (errtext + "\nDiscarded Lib ID: " + STR libid)    
            title:"DISCARD_LIB"
}

# load another library
CC "AdoScript" LISTBOX entries:(sAvailLibs) toksep:";" title:"Load Application Library" oktext:"Select" boxtext:"Choose Library ID:"
IF (endbutton = "ok") {
    SET applibid: -1
    CC "Core" GET_LIB_ID libname:(selection)
    CC "Core" LOAD_LIB libid:(libid)
    CC "AdoScript" INFOBOX (errtext + "\nAppLib-ID: " + (STR applibid))
            title:"LOAD_LIB"
}

{% endraw %}
```
{: .line-numbers}

