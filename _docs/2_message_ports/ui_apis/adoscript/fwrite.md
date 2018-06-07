---
layout: commandcall
category: CommandCall
title: "FWRITE"
tags: 1.3 1.5
---

FWRITE writes text to a file. There are two variants of usage, as follows

(1) Opening a file for writing (a), writing into that file (b), closing that file (c).

(2) Opening, writing and closing in one single command.

If FWRITE is called for many times with always the same file, variant (1) with one call of (1a), many of (1b) and finally one of (1c) is faster. Variant (2) is simpler to use as you do not have to take care that the file is opened before and closed after writing.

# Syntax:

(1a) Open a file for writing  
```adoscript
{% raw %}
CC "AdoScript" FWRITE open file:filename
					[ append:boolValue] [ binary:boolValue] [ base64:boolValue]

# --> RESULT ecode:intValue
{% endraw %}
```
{: .line-numbers}

(1b) Write into a file which has already be opened  
```adoscript
{% raw %}
CC "AdoScript" FWRITE text:strValue base64:boolValue

#--> RESULT ecode:intValue written:intValue .
{% endraw %}
```
{: .line-numbers}

(1c) Close a file which has been opened with FWRITE open  
```adoscript
{% raw %}
CC "AdoScript" FWRITE close

# --> RESULT ecode:intValue
{% endraw %}
```
{: .line-numbers}

(2) Open, write into and close at once  
```adoscript
{% raw %}
CC "AdoScript" FWRITE file:filename text:strValue
					[ append:boolValue] [ binary:boolValue] [ base64:boolValue]

#-->RESULT ecode:intValue written:intValue .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`file`|strValue, the name of the file|
|`text`|strValue, the text to be written into the file|
|`append`|boolValue; without specifying the argument append, a new file is created. If a file with the specified name already exists, it is deleted first. By passing the argument append, an exsiting file is not deleted but the text is appended at the end of the file.|
|`binary`|boolValue; without specifying the option binary (which then means text mode), "\n" (carriage return) is replaced by "\r\n". If you write strings which are containing just "\n" as newline separator, this replacement is correct, as in files "\r\n" is used as newline separator.|
|`base64`|boolValue, if specified, it means that the text string value is base64 encoded and shall be written decoded, i.e. the original (binary) text shall be written. It does not mean, that the text in the file will be base64 encoded.|

# Returns:  

|`ecode`|intValue, has the value 0 if no errors occured, otherwise a value != 0.|
|`written`|intValue, contains the number of bytes which have been written.|

# Remarks:

Relative paths relate to the installation directory.

Without specifying the argument append, a new file is created. If a file with the specified name already exists, it is deleted first. By passing the argument append, an exsiting file is not deleted but the text is appended at the end of the file.

Multi-line STRING attribute values in ADOxx already have "\r\n" as newline separator. So without specifying binary, you get "\r\r\n" as newline separator in the file. So you should specify binary if the written text is an multi-line STRING attribute value.

# See Also:  



Example:

