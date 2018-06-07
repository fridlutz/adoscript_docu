---
layout: commandcall
category: CommandCall
title: "UPDATE_MODEL_LIST"
tags: 1.3 1.5
---

The command UPDATE_MODEL_LIST updates the list of known models in the core.

# Syntax:  

```adoscript
{% raw %}
CC "Core" UPDATE_MODEL_LIST [ force: 1|0]

#--> ecode:intValue
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`force`|1|0|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success|

# Remarks:

The model list from the core is used as the base for the model list window that is e.g. displayed in the "Open model" dialog.

The update can take some time on systems with a few thousand models so it may be a good idea to add a waiting mouse cursor while performing this operation.

Using the boolean parameter force allows to enforce the update (i.e. refetching data from the DB is ensured). Without specifying the parameter (or using force:0) it might happen that the ADOxx internal handling detects no relevant change and therefore does not access the database.

# See Also:  

[UPDATE_SINGLE_MODEL](update_single_model.html "UPDATE_SINGLE_MODEL")  


Example 1:

```adoscript
{% raw %}

# update
CC "Core" UPDATE_MODEL_LIST force:1

IF ((ecode)!=0)
{
  CC "AdoScript" ERRORBOX ("Error "+(STR ecode)+" occured!")
  EXIT
}

CC "AdoScript" INFOBOX ("Updated model list successfully!")

{% endraw %}
```
{: .line-numbers}

