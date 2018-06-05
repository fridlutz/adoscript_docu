---
layout: commandcall
category: CommandCall
title: "ECODE_TO_ERRTEXT"
tags: 1.3 1.5
---

ECODE_TO_ERRTEXT converts a given eCode into a string which will be unique for each ADOxx version.

# Syntax:  

```adoscript
{% raw %}
CC "Core" ECODE_TO_ERRTEXT ecode:intValue

#--> RESULT errtext:strValue  .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`ecode`|intValue, contains the error code|

# Returns:  

|`errtext`|strValue, contains a textual representation of the ecode|

# Remarks:

This name is created by converting the internal name into a string. E.g. eCode 1 is internally called CLASS_NOT_EXISTING so the resulting errtext is  
"CLASS_NOT_EXISTING".  

If an unknown eCode is passed the resulting errtext will be "UNKNOWN". This function includes all Core Errorcodes and all DB Errorcodes.  

A complete list of all supported errorcodes

*  CORE_NO_ERROR
*  CLASS_NOT_EXISTING
*  RELATION_NOT_EXISTING
*  ATTRIBUTE_NOT_EXISTING
*  FACET_NOT_EXISTING
*  CLASSINSTANCE_NOT_EXISTING
* RELATIONINSTANCE_NOT_EXISTING
* ATTRIBUTEINSTANCE_NOT_EXISTING
* RECORDINSTANCE_NOT_EXISTING
* WRONG_CLASS_TYPE
* WRONG_RELATION_TYPE
* WRONG_ATTRIBUTE_TYPE
* WRONG_INSTANCE_TYPE
* WRONG_FACET_TYPE
* WRONG_SLOT_TYPE
* CLASS_IS_ABSTRACT
* INSTANCES_ALREADY_RELATED
* INSTANCES_NOT_RELATED
* SYSTEM_FACET_UNDELETABLE
* SYSTEM_ATTRIBUTE_UNDELETABLE
* SYSTEM_CLASS_UNDELETABLE
* WRONG_ENUMERATION_VALUE
* WRONG_TIME_VALUE
* WRONG_DISTRIBUTION_VALUE
* WRONG_PROGRAMCALL_VALUE
* WRONG_INTEGER_VALUE
* WRONG_DOUBLE_VALUE
* STRING_TOO_LONG
* LONGSTRING_TOO_LONG
* ATTRIBUTE_REGEXP_ERROR
* ATTRIBUTE_NUMDOMAIN_ERROR
* METAMODEL_ALREADY_EXISTS
* WE_METAMODEL_ALREADY_EXISTS
* BP_METAMODEL_ALREADY_EXISTS
* APPLICATIONLIBRARY_ALREADY_EXISTS
* WE_LIBRARY_ALREADY_EXISTS
* BP_LIBRARY_ALREADY_EXISTS
* APPLICATIONMODEL_ALREADY_EXISTS
* WE_MODEL_ALREADY_EXISTS
* BP_MODEL_ALREADY_EXISTS
* MODELVERSION_ALREADY_EXISTS
* METAMODEL_NOT_EXISTING
* WE_METAMODEL_NOT_EXISTING
* BP_METAMODEL_NOT_EXISTING
* APPLICATIONLIBRARY_NOT_EXISTING
* WE_LIBRARY_NOT_EXISTING
* BP_LIBRARY_NOT_EXISTING
* APPLICATIONMODEL_NOT_EXISTING
* WE_MODEL_NOT_EXISTING
* BP_MODEL_NOT_EXISTING
* CLASSOWNER_NOT_EXISTING
* INSTANCEOWNER_NOT_EXISTING
* NAME_IS_NOT_UNIQUE
* RELATION_NOT_ALLOWED
* METAMODEL_ALREADY_ATTACHED
* LIBRARY_ALREADY_ATTACHED
* MODEL_ALREADY_ATTACHED
* ATTACHMENT_NOT_ALLOWED
* NO_COMPONENT_ATTACHED
* LIBRARY_NOT_EXISTING
* MODEL_NOT_EXISTING
* METAMODEL_ALREADY_LOADED
* LIBRARY_ALREADY_LOADED
* MODEL_ALREADY_LOADED
* METAMODEL_NOT_LOADED
* LIBRARY_NOT_LOADED
* MODEL_NOT_LOADED
* COMPONENT_NOT_LOADED
* COMPONENT_NOT_EXISTING
* LOAD_ERROR
* NOT_IMPLEMENTED_YET
* ATTRIBUTEOWNER_NOT_EXISTING
* ACCESSMODE_CHANGED
* DELETION_NOT_ALLOWED
* SAVE_NOT_ALLOWED
* MODELTYPE_NOT_EXISTING
* WRONG_MODEL_TYPE
* NOTEBOOK_ATTRHANDLER_ERROR
* MODELTYPE_ATTRHANDLER_ERROR
* SIMMAP_ATTRHANDLER_ERROR
* LOAD_NOT_ALLOWED
* MOVE_NOT_ALLOWED
* CARDINALITY_HANDLER_ERROR
* RELNRDEF_HANDLER_ERROR
* COPYBUF_EXEC_INCONSISTENCY
* MULTIPLICITY_EXCEEDED
* INVALID_VERSION_STRING
* NAME_IS_TOO_LONG
* ERROR_APPMODEL_NAME_INVALID
* ERROR_APPMODEL_NAME_TOO_LONG
* ERROR_LIBRARY_NAME_INVALID
* ERROR_LIBRARY_NAME_TOO_LONG
* ERROR_MODELGROUP_NAME_INVALID
* ERROR_MODELGROUP_NAME_TOO_LONG
* INVALID_MODELTHREAD_ID
* ERROR_MODELTHREAD_NAME_INVALID
* ERROR_MODELTHREAD_NAME_TOO_LONG
* INVALID_MODELVERSION_ID
* ERROR_MODELVERSION_TOO_LONG
* INVALID_ATTRPROF_DIRECTORY
* INVALID_ATTRPROF_THREAD
* INVALID_ATTRPROF_VERSION
* ATTRPROF_DIRNAME_IS_NOT_UNIQUE
* ATTRPROF_DIRNAME_IS_INVALID
* ATTRPROF_THREADNAME_IS_NOT_UNIQUE
* ATTRPROF_THREADNAME_IS_INVALID
* ATTRPROF_VERSION_IS_NOT_UNIQUE
* INVALID_ATTRPROFREF_VALUE
* INVALID_INTERREF_VALUE
* SESSION_NOT_EXISTING
* SESSION_ALREADY_EXISTS
* SESSION_ALREADY_LOADED
* SESSION_NOT_LOADED
* DB_UNSPECIFIED_ERROR
* DB_INCORRECT_USER_SPECIFICATION
* DB_NOT_CONNECTED
* DB_COMMIT_WORK_FAILED
* DB_REFERENCED_CLASS_DOES_NOT_EXIST
* DB_ID_NOT_UNIQUE
* DB_VALUE_TOO_LONG
* DB_ELEMENT_NOT_FOUND
* DB_ROLLBACK_WORK_FAILED
* DB_LOCK_DOES_NOT_EXIST
* DB_USER_DOES_NOT_EXIST
* DB_INCORRECT_PASSWORD
* DB_USER_ALREADY_LOGGED_IN
* DB_OBJECT_ALREADY_LOCKED
* DB_NO_ONE_LOGGED_IN
* DB_USER_ALREADY_EXISTS
* DB_UNKNOWN_FACET_VALUE_TYPE
* DB_UNKNOWN_ATTRIBUTE_TYPE
* DB_DATABASE_ALREADY_EXIST
* DB_INST_GENERATE_METAMODELL_FAILED
* DB_ACTION_NOT_ALLOWOD_FROM_THIS_NODE
* DB_DATABASE_NOT_EXISTS
* DB_UNKNOWN_PATH
* DB_DATABASE_IN_USE
* DB_DBM_NOT_STARTED
* DB_TIMESTAMP_INVALID
* DB_TIMESTAMP_DATABASE_INVALID
* DB_LICENSE_ERROR
* DB_WRONG_CUSTOMER_NUMBER
* DB_INCORRECT_PASSWORDSTRING
* DB_INCORRECT_PASSWORDLENGTH
* DB_COMPONENT_NOT_AVAILABLE
* DB_MAX_USERS_REACHED
* DB_GROUP_NOT_EMPTY
* DB_NAME_ALREADY_IN_USE
* DB_NO_PERMISSION
* DB_REFERENCE_AREADY_EXISTS
* DB_GROUP_IS_ROOTGROUP
* DB_GROUP_IS_DEFAULT_GROUP
* DB_UNKNOWN_LIBRARY_TYPE
* DB_WRONG_SET_OF_MODELS
* DB_UNKNOWN_PROFILE_TYPE
* DB_WRONG_SCHEMA_VERSION
* DB_CHARSET_ERROR
* DB_INVALID_DB_NAME
* DB_SUPPORTFILE_ERROR
* DB_STD_APPLIB_CREATION_ERROR
* DB_OBJECT_NOT_UNIQUE
* DB_CONTAINER_NOT_EMPTY
* DB_REFERENCE_ERROR
* DB_CREATE_DOMAIN_ERROR
* DB_WRONG_SSO_STATUSTYPE
* DB_SSO_ALREADY_ACTIVATED
* DB_WRONG_LOGONNAME_TYPE
* DB_NO_CURR_USER_AND_DOMAIN
* DB_NO_USR_AUTHENT_AGAINST_SYS
* DB_NESTED_TRANSACTIONS_NOT_ALLOWED
* ADL_IMPORT_BIBIMPORT
* ADL_IMPORT_MOD_READONLY
* ADL_IMPORT_MOD_NO_ACCESS
* ADL_IMPORT_MOD_EDITED
* ADL_IMPORT_AP_EDITED
* ADL_IMPORT_INVALID_FORMAT
* ADL_IMPORT_MODGROUP_NOTEXISTING
* ADOSCRIPT_INVALID_PARAM_VALUE
* ADOSCRIPT_INVALID_PARAM_TYPE

# See Also:  


