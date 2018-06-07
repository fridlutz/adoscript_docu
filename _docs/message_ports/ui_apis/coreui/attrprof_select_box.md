---
layout: commandcall
category: CommandCall
title: "ATTRPROF_SELECT_BOX"
tags: 1.3 1.5
---

ATTRPROF_SELECT_BOX opens a dialog for selecting attriprofs and attrprofgroups.

# Syntax:  

```adoscript
{% raw %}
CC "CoreUI" ATTRPROF_SELECT_BOX	[ multi-sel [ count:intValue ] ] 
								[ with-mgmt-functions ] [ show-all-versions ] 
								[ apgroup-sel [ presel-apgroupids:strValue ] ] 
								[ filter:strValue ] [ presel-attrprofids:strValue ] 
								[ without-attrprofs ] [ title:strValue ] 
								[ boxtext:strValue ] [ oktext:strValue ]  
								[ w:intValue h:intValue ] 
								[min-w:intValue min-h:intValue ]

#--> RESULT ecode:intValue 
			endbutton:strValue 
			attrprofids:strValue 
			apgroupids:strValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`multi-sel`|modifier, if passed, the user can select multiple entries (attrprofs or attrproggroups) in the treelistbox. When it is not passed, only one entry can be selected.|
count - intValue, sets the valid amount of selected entries. (If 5 is passed the ok-button will only be enabled if 5 entries are selected.) A special case occurs when 0 is passed as count. In this case any number of selected entries is valid - even 0. (If count is not used at all, any number of selected entries larger than 0 are valid.)
|`with-mgmt-functions`|modifier, if passed, the dialog contains management buttons (copy, move, delete, ...) as shown in the example.|
|`show-all-versions`|modifier, if passed, the user can also select attrprofgroups in the treelistbox. If not, only attrprofs can be selected.|
|`apgroup-sel`|modifier, if passed, AP directories can be preselected with the argument presel-apgroupids.|
|`presel-apgroupids`|strValue, if passed, threads or versions can be preselected.|
|`filter`|strValue, if passed, only the attrprofclasses passed as value will be shown in the dialog.|
|`presel-attrprofids`|strValue|
|`without-attrprofs`|modifier, if passed, no attrprofs are displayed in the attrprof select box.|
|`title`|strValue, sets the dialog title|
|`boxtext`|strValue, the label of the treelistbox|
|`oktext`|strValue, the label of the ok-button|
|`w`|intValue, the width of the dialog|
|`h`|intValue, the height of the dialog|
|`min-w`|intValue, the minimal width of the dialog|
|`min-h`|intValue, the minimal height of the dialog|

# Returns:  

|`ecode`|intValue, the error code if an error occured or 0 otherwise|
|`endbutton`|strValue, specifies which button the user pressed to close the dialog. When the user pressed tht "Ok" button, it is set to "ok", when he pressed "Cancel" it is set to "cancel".|
|`attrprofids`|strValue, contains a space separated list of attrprof ids.|
|`apgroupids`|strValue, contain a space separated list of the attrprofgroupids the user has selected.|

# Remarks:

When the argument show-all-versions is passed, all attrprof versions are displayed and expanded in the treelistbox when the attrprof select box is opened.

# See Also:  



Example 1:

```adoscript
{% raw %}

CC "CoreUI" debug ATTRPROF_SELECT_BOX oktext:"Hit Me!" boxtext:"Please select your attrprofs:"
title:"ATTRPROG_SELECTBOX example" multi-sel apgroup-sel

{% endraw %}
```
{: .line-numbers}
Starts a dialog for selecting attrprofs  
![](/images/ATTRPROF_SELECT_BOX.png)

