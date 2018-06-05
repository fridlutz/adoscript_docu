---
layout: commandcall
category: CommandCall
title: "NEW_DOCU_EXPORT"
tags: 1.3 1.5
---

NEW_DOCU_EXPORT starts the documentation generation for a given set of models.

# Syntax:  

```adoscript
{% raw %}
CC "Documentation" NEW_DOCU_EXPORT	strValue Source 
									[ filename:strValue ] [ filetype: sgml | xml ]
									[ linebreak:strValue ]
									[ NoInterRefWarnings ] [ silentmode ]
									[ NoRecordRows ] [ strong-reference-check [: 1|0] ]
									[ get-offline-target-instances ]
									[ with-interref-target-ids[: 1|0] ]
									[ maxw:intValue ] [ maxh:intValue ] .


Source :		SourceModels | SourceRecord .

SourceModels :	[ modelids:strValue ] [ refmodelids:strValue ] .

SourceRecord :	objid:id attrid:id .

NoInterRefWarnings :	no-interref-warnings[: 1|0] |
						no-interref-warnings:attribute:attrName .

NoRecordRows :	no-record-rows[: 1|0] |
				no-record-rows:attributes:strValue .

#--> RESULT ecode:intValue 
			canceled:intValue 
			gfxscaling:strValue .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`<main_parameter>`|strValue, the name of the menuentry for the documentation generation in the documentation menu has to be specified.|
|`filename`|strValue, string value containing the target file name and path|
|`filetype`| sgml | xml, the type of the export file; default is sgml. When filetype:xml is specified, the export file is in XML format. This is similar to SGML. However, all tags are closed and the encoding is always UTF8. (The tags which are not closed in SGML are &lt;SPOT&gt; and &lt;ATTRSPOT&gt;.)|
|`linebreak`|strValue, used for changing the linebreak characters.|
|`silentmode`|modifier if specified, all messages at the UI are suppressed while documentation is generated.|
|`strong-reference-check`|if set, the export component checks for any exported reference (INTERREF entry) which is valid on core level, whether the referenced model also exists on database level. By default such references do not appear as broken, although following such a reference (= loading the referenced model) is not possible. The default behavior is exactly the behavior of the rich client. The references on Core level become up-to-date only on updating of the model list.|
|`get-offline-target-instances`|modifier, if specified, for references to instances the VALUE tag in the SGML file is written with an attribute OFFLINETARGETINSTANCEID.|
|`with-interref-target-ids`|0|1|
|`maxw`|intValue, specifies the maximum width of generated graphics (in pixels). When the generated model graphics would actually be larger, the scaling factor is reduced automatically, so that the generated graphics has at most the specified maximum width.|
|`maxh`|intValue, specifies the maximum height of generated graphics (in pixels). When the generated model graphics would actually be larger, the scaling factor is reduced automatically, so that the generated graphics has at most the specified maximum height.|
|`modelids`|strValue, contains the IDs of all main models that should be exported, separated by blank spaces.|
|`refmodelids`|strValue, contains the IDs of all referenced models that should be exported, separated by blank spaces.|
|`objid`|id|
|`attrid`|id|
|`no-interref-warnings`|if present suppresses the error messages caused by dangling references it the exporting is being performed with the option "with referenced models". Instead of passing a bool value directly, you can also specify the name of an integer attribute of the _LibraryMetaData_ class, whose value is interpreted then.|
|`no-record-rows`|if specified, record rows are not exported. This may be used for performance enhancement, when record contents are not needed momentarily. Alternatively you can specify a list of record attribute IDs, for which no rows are exported. The content of a single records can be exported by specifying the containing object (objid) and the record attribute (attrid) as source. Note that the related model must be loaded.|

# Returns:  

|`ecode`|intValue, is 1 in case of success or 0 otherwise.|
|`canceled`|0|1, if ecode != 0 and the generation has been canceled by the user, canceled has the value 1, otherwise 0.|
|`gfxscaling`|strValue, gives you information on if and how automitic downsizing has been applied. It is a string containing an array value which contains the actual scaling factors for each generated graphics file. Each element of that array represents one graphics file and is again an array, consisting of three elements: a model id, a dpi value and a scaling factor. The scaling factor normally is 1.0 for each generated graphics file. If a graphics file could not be generated with the desired resolution, automatic downsizing is applied, using a smaller scaling factor.|

# Remarks:

When the file type is XML, since version 1.3 by default no linebreaks are written between tags, while for older versions and still for SGML newline ("\n") characters are written, so that the export file can easier be read using a normal text editor. The linebreak string can be changed with linebreak, e.g. linebreak:"" or linebreak:"\n".

When modelids or refmodelids is not specified the model lists that have been evaluated the last time the export dialog has been opened will be used. To avoid this, pass an empty string (modelids:"" or refmodelids:"").  
When only modelids and not refmodelids has been specified, no referenced model list of the last export dialog will be used.

The value "{% raw %}{{4711, 96, 0.8}, {4711, 72,1.0}}{% endraw %}" for gfxscaling means that two graphics files have been generated for model id 4711. The first one should have been generated with 96 dpi, but has been downsized with scaling factor 0.8. The second graphics file has successfully been generated with 72 dpi. Unfortunately, gfxscaling is not an array but a string containing an array value. To convert that string into a real array value, write SET gfxscale:(VAL ("(" + gfxscale + ")")).

# See Also:  

[DOCU_EXPORT](docu_export.html "DOCU_EXPORT")  


Example 1:

The following lets the user select models in the export dialog. Then two documentations are generated with the call NEW_DOCU_EXPORT: one for **html** and one for **rtf** documentation.  
```adoscript
{% raw %}

CC "Documentation" EXEC_EXPORTDIALOG "RTF, HTML & ADL Export"
    filedescription:"HTML/RTF/ADL Files" fileextension:"**.adl"
IF (ecode <= 0) {
    CC "AdoScript" INFOBOX "Export canceled"
    EXIT
}
SET basename:(copy(filename, 0, LEN filename - 4))

CC "Documentation" NEW_DOCU_EXPORT "HTML-Generierung..."
    filename:(basename+".html")
    modelids:(selmodelids) refmodelids:(refmodelids)
IF (ecode != 0) {
    IF (canceled = 1) {
        CC "AdoScript" INFOBOX "Export canceled"
    } ELSE {
        CC "AdoScript" INFOBOX "An error occured."
    }
    EXIT
}
CC "Documentation" NEW_DOCU_EXPORT "RTF-Generierung..." 
    filename:(basename+".rtf")
    modelids:(selmodelids) refmodelids:(refmodelids)
IF (ecode != 0) {
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

