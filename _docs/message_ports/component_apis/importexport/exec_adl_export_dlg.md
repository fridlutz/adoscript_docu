---
layout: commandcall
category: CommandCall
title: "EXEC_ADL_EXPORT_DLG"
tags: 1.3 1.5
---

EXEC_ADL_EXPORT_DLG shows the ADL export dialog and also performs the export specified by the user (if the dialog has not been cancelled).

# Syntax:  

```adoscript
{% raw %}
CC "ImportExport" EXEC_ADL_EXPORT_DLG
{% endraw %}
```
{: .line-numbers}

# Parameters:  

none

# Returns:  

none

# Remarks:

This command has the same effect as if the user selects "ADL Import" at the user interface. The running AdoScript gets no information whether anything and what has been exported.

For custom export formats (e.g. XML) there is also a command SHOW_EXPORT_DIALOG. That command shows just the dialog without doing an export. Therefore all selected options are returned.

Another export dialog is provided by the "Documentation" Messageport (CC "Documentation" EXEC_EXPORTDIALOG).

# See Also:  

[SHOW_EXPORT_DIALOG](show_export_dialog.html "SHOW_EXPORT_DIALOG")  
[EXEC_EXPORTDIALOG](exec_exportdialog.html "EXEC_EXPORTDIALOG")  
[EXEC_ADL_IMPORT_DLG](exec_adl_import_dlg.html "EXEC_ADL_IMPORT_DLG")  


