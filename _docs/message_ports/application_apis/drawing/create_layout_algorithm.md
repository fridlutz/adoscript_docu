---
layout: commandcall
category: CommandCall
title: "CREATE_LAYOUT_ALGORITHM"
tags: 1.3 1.5
---

CREATE_LAYOUT_ALGORITHM dynamically creates a new layout algorithm instance.

# Syntax:  

```adoscript
{% raw %}
CC "Drawing" CREATE_LAYOUT_ALGORITHM WithoutSwimlanes | WithSwimlanes

WithoutSwimlanes :	"Without swimlanes" [ name:strValue ]
										{ name_<langcode>:strValue }
										[ orientation:horizontal | vertical ]
										[ raster-width:measureValue ]
										[ raster-height:measureValue ]

WithSwimlanes :		"With swimlanes"	[ name:strValue ]
										{ name_<langcode>:strValue }
										swimlane-creation-attr:strValue
										swimlane-classname:strValue
										[ raster-width:measureValue ]
										[ raster-height:measureValue ] 

# --> RESULT ecode:intValue 
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`name`|strValue, the name of the layout algorithm|
|`name_<langcode>`|strValue, the name of the layout algorithm in the language specified by the langcode|
|`orientation`|Orientation|
|`raster-width`|measureValue, cm or pt|
|`raster-height`|measureValue, cm or pt|
|`swimlane-creation-attr`|strValue|
|`swimlane-classname`|strValue|
|`horizontal`|modifier|
|`vertical`|modifier|

# Returns:  

|`ecode`|intValue, contains the error code or is 0 in case of success.|

# Remarks:

With this command layout algorithm instances as described in document.  
Library attribute "Default settings -- layout algorithms can be created dynamically via AdoScript instead of statically via library attribute. The parameters have the same meaning as described in the linked document for static layout algorithm instances.

Dynamic layout algorithm instances are not accessible via UI and should be deleted (CC "Drawing" DELETE_LAYOUT_ALGORITHM) after application.

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "Modeling" GET_ACT_MODEL
CC "Drawing" CREATE_LAYOUT_ALGORITHM "Without swimlanes"
        name:"temp"	orientation:horizontal
        raster-width:6cm raster-height:4cm
CC "Drawing" EXEC_LAYOUT_ALGORITHM name:"temp" modelid:(modelid)
CC "Drawing" DELETE_LAYOUT_ALGORITHM name:"temp"

{% endraw %}
```
{: .line-numbers}

