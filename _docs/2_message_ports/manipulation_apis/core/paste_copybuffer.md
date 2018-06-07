---
layout: commandcall
category: CommandCall
title: "PASTE_COPYBUFFER"
tags: 1.3 1.5
---

PASTE_COPYBUFFER pastes the content of a copy buffer object into the given model.

# Syntax:  

```adoscript
{% raw %}
CC "Core" PASTE_COPYBUFFER index:intValue modelid:intValue moverefs: [1|0}]

#--> RESULT ecode:intValue instids:strValue relinstids:strValue reftext:strValue .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`index`|intValue|
|`moverefs`|1|0, is specified without value, or with any value != 0, all incoming INTERREFs to the copied objects are changed to INTERREFs to the pasted objects.|


# Returns:  

|`ecode`|intValue, is 0 in case of success or -1 if no copy buffer with the given ID exists. Any other ecode value is a valid core errorcode.|
|`instids`|strValue, a list of instance IDs separated by blanks|
|`relinstids`|strValue, a list of relation instance IDs separated by blanks|
|`reftext`|strValue, lists all incoming INTERREFs. See GET_INCOMING_INTERREFs for more details.|

# Remarks:

Call this method with a copy buffer object you created with CREATE_COPYBUFFER and filled with FILL_COPYBUFFER.

You can use this method to paste the content to as many models you like.

If the modeltype of the source objects and the target model do not match nothing is pasted. Only if you are referencing the same classes (by ID, not by name!) party maybe pasted.

Ensure to delete a copy buffer with DELETE_COPYBUFFER, when it is no longer needed.

# See Also:  

[FILL_COPYBUFFER](fill_copybuffer.html "FILL_COPYBUFFER")  
[DELETE_COPYBUFFER](delete_copybuffer.html "DELETE_COPYBUFFER")  
[CREATE_COPYBUFFER](create_copybuffer.html "CREATE_COPYBUFFER")  
[GET_INCOMING_INTERREFS](get_incoming_interrefs.html "GET_INCOMING_INTERREFS")  


Example 1:

```adoscript
{% raw %}

## 1. take the currently open model
## 2. copy all objects and all relation instances
## 3. create a new model
## 4. paste the objects twice
## 5. save and discard the model
## 6. open the new model in view mode
## 7. select the objects that were pasted second

CC "Modeling" GET_ACT_MODEL
IF (modelid = -1)
{
  CC "AdoScript" INFOBOX ("Currently no model window exists.")
  EXIT
}

## get all instances
CC "Core" GET_ALL_OBJS modelid:(modelid)
SETL a_instids:(objids)

## get all connectors
CC "Core" GET_ALL_CONNECTORS modelid:(modelid)
SETL a_relinstids:(objids)

## copy all objects
CC "Core" CREATE_COPYBUFFER index:0
CC "Core" FILL_COPYBUFFER index:0 instids:(a_instids) relinstids:(a_relinstids)

## select a target model group
CC "CoreUI" MODEL_SELECT_BOX without-models mgroup-sel title:"Select at least one target modelgroup"
SETL a_mgroupids:(mgroupids)

## build a list with all modeltypes
CC "Core" GET_ALL_MODELTYPES sep:"@"
SET a_modeltypes:(modeltypes)

CC "AdoScript" TLB_CREATE title:"Select a modeltype" flat:1 sorted:1 searchable:1 no-cancel:1 no-help:1 multi-sel:0
SETL a_id:0
FOR a_mt in:(a_modeltypes) sep:"@"
{
  CC "AdoScript" TLB_INSERT id:(a_id) text:(a_mt)
  SETL a_id:(a_id + 1)
}
CC "AdoScript" TLB_SHOW
SETL a_mt:(token (a_modeltypes, VAL selectedids, "@"))

SET a_dstmodelid:0

SET ecode:1
WHILE (ecode != 0)
{
  ## let the user enter a new modelname
  CC "AdoScript" EDITFIELD title:("New model of modeltype " + a_mt) caption:"~Modelname:"
  IF (ecode = 0)
  {
    SETL a_name:(text)
    CC "Core" CREATE_MODEL modeltype:(a_mt) modelname:(a_name) version:"" mgroups:(a_mgroupids)
    IF (ecode = 0)
    {
      SET a_dstmodelid:(modelid)
    }
    ELSE
    {
      CC "AdoScript" ERRORBOX ("An error occured creating the new model: " + errtext) ok
    }
  }
  ELSE
  {
    CC "AdoScript" INFOBOX ("Aborted by user!")
    EXIT
  }
}

## paste twice in new model and that's it
CC "Core" PASTE_COPYBUFFER index:0 modelid:(a_dstmodelid)
CC "Core" PASTE_COPYBUFFER index:0 modelid:(a_dstmodelid)
SETL g_acreatedinstids:(instids)
SETL g_acreatedrelinstids:(relinstids)

CC "Core" DELETE_COPYBUFFER index:0

## save and discard model
CC "Core" SAVE_MODEL modelid:(a_dstmodelid)
CC "Core" DISCARD_MODEL modelid:(a_dstmodelid)

## open new model in modeling
CC "Modeling" OPEN modelids:(STR a_dstmodelid)

## dye all remembered objects
FOR a_id in:(g_acreatedinstids)
{
  CC "Modeling" SELECT objid:(VAL a_id)
}
FOR a_id in:(g_acreatedrelinstids)
{
  CC "Modeling" SELECT objid:(VAL a_id)
}

{% endraw %}
```
{: .line-numbers}

