---
layout: commandcall
category: CommandCall
title: "GET_ALL_APPLIBS"
tags: 1.3 1.5
---



# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_ALL_APPLIBS

#--> RESULT ecode:intValue errtext:strValue applibids:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

none

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`errtext`|strValue, gives the reason of failure.|
|`applibids`|strValue, a string of library ids separated by spaces|

# Remarks:

This command is only available within **ADOxx Development Toolkit**.

# See Also:  



Example 1:

```adoscript
{% raw %}

# show all available applicataion libraries
SET sLibs: ""
SET sAvailLibs: ""
CC "Core" GET_ALL_APPLIBS
FOR id in:(applibids)
{
  CC "Core" GET_LIB_NAME libid:(VAL id)
  CC "Core" GET_LIB_ID libname:(libname)
  SET sLibs: (sLibs + STR libid + ":\t" + libname + " [ " + type + " ] " + "\n")
  SET sAvailLibs: (sAvailLibs + libname + ";")
}
CC "AdoScript" INFOBOX (sLibs) title:"GET_ALL_LIBS"

# show the current application library
SET applibid: -1
SET applib: ""
CC "Core" GET_CURRENT_LIBS
CC "AdoScript" INFOBOX ("Current application library:\n" + applib) title:"GET_CURRENT_LIBS"

# discard the current library
IF (applibid > 0)
{
  CC "Core" DISCARD_LIB
  CC "AdoScript" INFOBOX (errtext + "\nDiscarded Lib ID: " + STR libid) title:"DISCARD_LIB"
}

# load another library
CC "AdoScript" LISTBOX entries:(sAvailLibs) toksep:";" title:"Load Application Library" oktext:"Select" boxtext:"Choose Library ID:"
IF (endbutton = "ok")
{
  SET applibid: -1
  CC "Core" GET_LIB_ID libname:(selection)
  CC "Core" LOAD_LIB libid:(libid)
  CC "AdoScript" INFOBOX (errtext + "\nAppLib-ID: " + (STR applibid)) title:"LOAD_LIB"
}

{% endraw %}
```
{: .line-numbers}

- get and show all available application libraries  
- show the currently loaded application library  
- discard this library  
- let the user select a new library  
- load what the user has selected  
