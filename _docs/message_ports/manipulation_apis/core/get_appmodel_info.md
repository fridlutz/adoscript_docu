---
layout: commandcall
category: CommandCall
title: "GET_APPMODEL_INFO"
tags: 1.3 1.5
---



# Syntax:  

```adoscript
{% raw %}
CC "Core" GET_APPMODEL_INFO appmodelid:id .

#--> RESULT ecode:intValue 
			appmodelname:strValue 
			bpmodelids:strValue 
			wemodelid:id 
			onthreads:[0|1] 
			onversions:[0|1]
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`appmodelid`|intValue, the ID of the application model|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`appmodelname`|strValue, the name of the application model|
|`bpmodelids`|strValue, a space-separated list of the Dynamic models of which the ApplicationModel consists|
|`wemodelid`|intValue, the ID of the ApplicationModel's Static model (must be exactly one!).|
|`onthreads`|[0|1], is 1 if the ApplicationModel is defined on threads else it is 0. onthreads can be only 1 if versioning is enabled!|
|`onversions`|[0|1], is 1 if the ApplicationModel is defined on versions else it is 0. onversions is always 1 in non-versioned libraries!|

# Remarks:



# See Also:  



Example 1:

```adoscript
{% raw %}

# Assume there is an ApplicationModel "Test"
SET appmod_name:"Test"

# retrieve the ID of the appmodel
CC "Core" GET_APPMODEL_ID appmodelname:(appmod_name)
IF (ecode != 0)
{
  CC "AdoScript" ERRORBOX ("An ApplicationModel with the name \"" + appmod_name + "\" does not exist!") ok
}
ELSE
{
  SET id:(appmodelid)

  # Take the IDs returned from GET_APPMODEL_ID
  CC "Core" GET_APPMODEL_INFO appmodelid:(id)

  # build the result string
  SET msg:("Information for the ApplicationModel \"" + appmod_name + "\"\n\n")
  SET msg:(msg + "ID: " + STR id + "\n")
  SET msg:(msg + "Name: " + appmodelname + "\n")

  # is the AppModel defined on threads? - only possible if versioning is enabled!
  IF (onthreads = 1)
  {
    SET msg:(msg + "Is defined on threads\n")
  }
  ELSE
  {
    SET msg:(msg + "Is NOT defined on threads\n")
  }

  # is the AppModel defined on versions? - default in non versioned libraries!
  IF (onversions = 1)
  {
    SET msg:(msg + "Is defined on versions\n")
  }
  ELSE
  {
    SET msg:(msg + "Is NOT defined on versions\n")
  }

  # add BP model names:
  SET msg:(msg + "BP models:\n")
  FOR bpm in:(bpmodelids)
  {
    CC "Core" GET_MODEL_INFO modelid:(VAL bpm)
    SET msg:(msg + "\t" + modelname + " " + ver + "\n")
  }

  # add WE model
  SET msg:(msg + "WE model:\n")
  CC "Core" GET_MODEL_INFO modelid:(wemodelid)  # wemodelid was return from GET_APPMODEL_INFO
  SET msg:(msg + "\t" + modelname + " " + ver + "\n")

  # show the resulting information
  CC "AdoScript" INFOBOX (msg)
}

{% endraw %}
```
{: .line-numbers}

