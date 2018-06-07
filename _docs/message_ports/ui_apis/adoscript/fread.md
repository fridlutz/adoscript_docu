---
layout: commandcall
category: CommandCall
title: "FREAD"
tags: 1.3 1.5
---

FREAD reads the content of a file.

# Syntax:  

```adoscript
{% raw %}
CC "AdoScript" FREAD file:strValue [ binary:boolValue ] [ base64:boolValue ]

# -->RESULT text:strValue ecode:intValue .
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`file`|strValue, the name of the file|
|`binary`|boolValue, specifies whether the file should be read in binary mode (binary:1) or in text mode (binary:0). In text mode, all line breaks in the scanned text are automatically set to '\n'. In binary mode all line breaks stay the way they are.|
|`base64`|boolValue, if specified, it means that the resulting text value shall be the base64 encoded content of the file instead of the original (binary) content.|

# Returns:  

|`text`|strValue, contains the content of the file.|
|`ecode`|intValue, has the value 0 if no errors occured, a value different than 0 if an error occured.|

# Remarks:

Relative paths relate to the installation directory.  

Note that the parameter binary does not mean that binary files can be read into a string! A binary file may contain null characters which are used as end character in strings. Binary files can just be read as a base64 encoded string (see below).

If ecode has the value 2, the the file is too large to store its content in a string variable. The maximum length for a string variable is 2^31 characters (~2GB).

# See Also:  



Example:

