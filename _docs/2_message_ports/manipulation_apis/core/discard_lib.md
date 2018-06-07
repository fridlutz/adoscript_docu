---
layout: commandcall
category: CommandCall
title: "DISCARD_LIB"
tags: 1.3 1.5
---

DISCARD_LIB unloads the currently loaded application library.

# Syntax:  

```adoscript
{% raw %}
CC "Core" DISCARD_LIB

#--> RESULT ecode:intValue libid:id .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

none

# Returns:  

|`ecode`|intValue, if the current application library could be discarded successfully (ecode is 0)|
|`libid`|intValue, holds the ID of the discarded application library.|

# Remarks:

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

