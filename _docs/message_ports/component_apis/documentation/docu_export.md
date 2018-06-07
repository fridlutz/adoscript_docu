---
layout: commandcall
category: CommandCall
title: "DOCU_EXPORT"
tags: 1.3 1.5
---



# Syntax:  

```adoscript
{% raw %}
CC "Documentation" DOCU_EXPORT strValue	[ filename:strValue ]
										[ modelids:idCont ] [ refmodelids:idCont  ]
										[ NoInterRefWarnings ] [ silentmode ]
										[ get-offline-target-instances ]
										[ maxw:intValue ] [ maxh:intValue ]
										[ max-size:intValue ]

NoInterRefWarnings :	no-interref-warnings |
						no-interref-warnings:boolValue |
						no-interref-warnings:attribute:attrName .

#--> RESULT ecode:intValue 
			canceled:boolValue 
			gfxscaling:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`<main_parameter>`|strValue,|
|`filename`|strValue, string value containing the target file name and path|
|`modelids`|idCont, is a string value containing model IDs of the models to be exported separated by " " (blank)|
|`refmodelids`|idCont, is a string value containing related model IDs separated by " " (blank)|
|`no-interref-warnings`|modifier; if present suppresses the error messages caused by dangling references it the exporting is being performed with the option "with referenced models"|
|`silentmode`|modifier, if specified, all messages at the UI are suppressed while documentation is generated.|
|`get-offline-target-instances`|modifier, if specified, for references to instances the VALUE tag in the SGML file is written with an attribute OFFLINETARGETINSTANCEID.|
|`maxw`|intValue, specifies the maximum width of generated graphics (in pixels). When the generated model graphics would actually be larger, the scaling factor is reduced automatically, so that the generated graphics has at most the specified maximum width.|
|`maxh`|intValue, specifies the maximum height of generated graphics (in pixels). When the generated model graphics would actually be larger, the scaling factor is reduced automatically, so that the generated graphics has at most the specified maximum height.|
|`max-size`|intValue, allows to specify a restriction concerning the graphics size in square pixels. This option will keep the aspect ratio of the image by scaling down each dimension by the same amount. Especially if the "shape" of the image is not known in advance, this parameter option might be better suited than using maxw and maxh.|

# Returns:  

|`ecode`|intValue, is 1 in case of success or 0 otherwise.|
|`canceled`|0|1|
|`gfxscaling`|strValue, gives you information on if and how automitic downsizing has been applied. It is a string containing an array value which contains the actual scaling factors for each generated graphics file. Each element of that array represents one graphics file and is again an array, consisting of three elements: a model id, a dpi value and a scaling factor. The scaling factor normally is 1.0 for each generated graphics file. If a graphics file could not be generated with the desired resolution, automatic downsizing is applied, using a smaller scaling factor.|

# Remarks:

Attention!!! eCode = 1 means ok, eCode = 0 means error!  
The new command  NEW_DOCU_EXPORT does the same as DOCU_EXPORT, but complies with the ecode convention (i.e. ecode 0 means OK and != 0 means error).

The value "{% raw %}{{4711, 96, 0.8}, {4711, 72,1.0}}{% endraw %}" for gfxscaling means that two graphics files have been generated for model id 4711. The first one should have been generated with 96 dpi, but has been downsized with scaling factor 0.8. The second graphics file has successfully been generated with 72 dpi. Unfortunately, gfxscaling is not an array but a string containing an array value. To convert that string into a real array value, write SET gfxscale:(VAL ("(" + gfxscale + ")")).

# See Also:  

[NEW_DOCU_EXPORT](new_docu_export.html "NEW_DOCU_EXPORT")  


Example 1:

The following lets the user select models in the export dialog. Then two documentations are generated with the call DOCU_EXPORT: one for **html** and once for **rtf** documentation.  
```adoscript
{% raw %}

CC "Documentation" EXEC_EXPORTDIALOG "RTF, HTML & ADL Export"
    filedescription:"HTML/RTF/ADL Files" fileextension:"**.adl"
IF (ecode <= 0) {
    CC "AdoScript" INFOBOX "Export canceled"
    EXIT
}
SET basename:(copy(filename, 0, LEN filename - 4))

CC "Documentation" DOCU_EXPORT "HTML-Generierung..."
    filename:(basename+".html")
    modelids:(selmodelids) refmodelids:(refmodelids)
# ecode == 0 means error
IF (ecode == 0) {
    IF (canceled = 1) {
        CC "AdoScript" INFOBOX "Export canceled"
    } ELSE {
        CC "AdoScript" INFOBOX "An error occured."
    }
    EXIT
}
CC "Documentation" DOCU_EXPORT "RTF-Generierung..." 
    filename:(basename+".rtf")
    modelids:(selmodelids) refmodelids:(refmodelids)
# ecode == 0 means error
IF (ecode == 0) {
    IF (canceled = 1) {
        CC "AdoScript" INFOBOX "Export canceled"
    } ELSE {
        CC "AdoScript" INFOBOX "An error occured."
    }
    EXIT
}

{% endraw %}
```
{: .line-numbers}

