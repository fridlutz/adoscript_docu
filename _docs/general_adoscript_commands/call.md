---
layout: commandcall
category: CommandCall
title: "CALL"
tags: 1.3 1.5
---

CALL calls a function in a dynamic link library (DLL).

# Syntax:  

```adoscript
{% raw %}
CALL dll:strExpr function:strExpr { InputParam }
				[ result:varName ] [ freemem:strValue ]

InputParam :	varname:anyExpr
{% endraw %}
```
{: .line-numbers}

# Parameters:  

|`dll`|strExpr, the name of the DLL|
|`function`|strExpr, the name of the function using the C declaration syntax.|
|`varname`|anyExpr, a variable as in the definition of the function.|
|`result`|varName, the return value of the called function is assigned to the run-time variable specified with the atribute result or to the run-time variable result if this specification is omitted.|
|`freemem`|strValue, if specified, the memory allocated by the DLL is freed after the function has been executed|

# Returns:  

|`ecode`|intValue, Contains the error code or is 0 in case of success.|
|`errtext`|strValue, contains a textual representation of the ecode|

# Remarks:

The name of the DLL is specified with dll, the function is specified with function using the C function declaration syntax (see the sample below). A combination of a return value type and (zero, one ore more) parameter value types is called signature. Supported return value types of a called function are: void, long, double, char**. Supported parameter value types are: long, double, char**, long**, double**, char****, where the first three are input and the last three are output parameters. All possible signatures of these types are supported.

If the return value type is char** or a parameter value type is char**** the DLL is allocating memory to hold the string value. The freeing of this memory has to be done within the DLL too, but the "freemem" call is done by AdoScript. By default, AdoScript calls a function freemem (char**) of the DLL if the memory is no longer needed (i.e. the string has been copied to an AdoScript run-time variable). If another function is specified with freemem in the CALL statement that function is called instead.

All input paramerers are passed as attributes with the CALL statement using the same names as at the formal parameters in the function declaration. The output parameters are assigned to run-time variales, also with the same names as at the formal parameters in the function declaration. The return value of the called function is assigned to the run-time variable specified with the atribute result or to the run-time variable result if this specification is omitted.

In a running AdoScript at most one DLL is loaded at a time. At the first execution of a CALL in a running AdoScript the DLL is loaded. For any following CALL with the same DLL the loaded DLL is reused. If another DLL is called, or the running AdoScript terminates, a previously loaded DLL is unloaded. With this behavior data can be build up inside a DLL using multiple calls. Although DLLs are freed at termination of an AdoScript, it is a good style to provide and use a cleanup function if data is stored inside a DLL.

# See Also:  



Example 1:

Calling a DLL from AdoScript  
```adoscript
{% raw %}

# Functions returning void with input params only!
CALL dll:"dll1.dll" function:"void f_void_void ()"
CALL dll:"dll1.dll" function:"void f_void_long (long n)" n:4242
CALL dll:"dll1.dll" function:"void f_void_double (double d)" d:3.14
CALL dll:"dll1.dll" function:"void f_void_charptr (char **p)" p:"Hallo Welt"
CALL dll:"dll1.dll" function:"void f_void_long_double_charptr (long n, double d, char** p)" n:4711 d:2.34 p:"Yippie"

# Functions returning long with input params only!
CALL dll:"dll1.dll" function:"long f_long_void ()" result:bla
CC "AdoScript" INFOBOX (STR bla)
CALL dll:"dll1.dll" function:"long f_long_long (long n)" result:bla n:4242
CC "AdoScript" INFOBOX (STR bla)
CALL dll:"dll1.dll" function:"long f_long_double (double d)" result:bla d:3.14
CC "AdoScript" INFOBOX (STR bla)
CALL dll:"dll1.dll" function:"long f_long_charptr (char **p)" result:bla p:"Hallo Welt"
CC "AdoScript" INFOBOX (STR bla)
CALL dll:"dll1.dll" function:"long f_long_long_double_charptr (long n, double d, char** p)" result:bla n:4711 d:2.34 p:"Yippie"
CC "AdoScript" INFOBOX (STR bla)

# Functions returning double with input params only!
CALL dll:"dll1.dll" function:"double f_double_void ()" result:bla
CC "AdoScript" INFOBOX (STR bla)
CALL dll:"dll1.dll" function:"double f_double_long (long n)" result:bla n:4242
CC "AdoScript" INFOBOX (STR bla)
CALL dll:"dll1.dll" function:"double f_double_double (double d)" result:bla d:3.14
CC "AdoScript" INFOBOX (STR bla)
CALL dll:"dll1.dll" function:"double f_double_charptr (char **p)" result:bla p:"Hallo Welt"
CC "AdoScript" INFOBOX (STR bla)
CALL dll:"dll1.dll" function:"double f_double_long_double_charptr (long n, double d, char** p)" result:bla n:4711 d:2.34 p:"Yippie"
CC "AdoScript" INFOBOX (STR bla)

# Functions with output params only!
CALL dll:"dll1.dll" function:"void f_get_long (long** bla)"
CC "AdoScript" INFOBOX (STR bla)
CALL dll:"dll1.dll" function:"void f_get_double (double** bla)"
CC "AdoScript" INFOBOX (STR bla)
CALL dll:"dll1.dll" function:"void f_get_charptr (char**** bla)"
CC "AdoScript" INFOBOX (bla)

# Mixture
CALL dll:"dll1.dll" function:"void f_all (long nin, double din, char** pin, long** nout, double** dout, char**** pout)" nin:2 din:3.14 pin:"It works!"
CC "AdoScript" INFOBOX ("nout: " + STR nout + "\ndout: " + STR dout + "\npout: " + pout)
{% endraw %}
```
{: .line-numbers}


The Sourcecode of the DLL "dll1.dll" (compile with Visual C++, using the commandline cl -LD dll1.cxx):

```adoscript
{% raw %}
#include <stdio.h>
#include <windows.h>

#pragma comment(lib, "user32.lib")

#define _Export extern "C" __declspec(dllexport)
#define MB(x) MessageBox(NULL, x, "dll1", MB_OK);

char sBuf[2048];

needed by AdoScript
_Export void __cdecl freemem(char **p) {
    MB("freemem(p)");
    free(p);
}

//Functions returning void with input params only!

_Export void __cdecl f_void_void() {
    MB("f_void_void()");
}

_Export void __cdecl f_void_long(long n) {
    sprintf(sBuf, "f_void_long(%d)", n);
    MB(sBuf);
}

_Export void __cdecl f_void_double(double d) {
    sprintf(sBuf, "f_void_double(%.2f)", d);
    MB(sBuf);
}

_Export void __cdecl f_void_charptr(char **s) {
    sprintf(sBuf, "f_void_charptr(%s)", s);
    MB(sBuf);
}

_Export void __cdecl f_void_long_double_charptr(long n, double d, char **s) {
    sprintf(sBuf, "f_void_long_double_charptr (%d, %.2f, %s)", n, d, s);
    MB(sBuf);
}

//Functions returning long with input params only!

_Export long __cdecl f_long_void() {
    MB("f_long_void()");
    return 666;
}

_Export long __cdecl f_long_long(long n) {
    sprintf(sBuf, "f_long_long (%d)", n);
    MB(sBuf);
    return 667;
}

_Export long __cdecl f_long_double(double d) {
    sprintf(sBuf, "f_long_double (%.2f)", d);
    MB(sBuf);
    return 668;
}

_Export long __cdecl f_long_charptr(char **s) {
    sprintf(sBuf, "f_long_charptr(%s)", s);
    MB(sBuf);
    return 669;
}

_Export long __cdecl f_long_long_double_charptr(long n, double d, char **s) {
    sprintf(sBuf, "f_long_long_double_charptr(%d, %.2f, %s)", n, d, s);
    MB(sBuf);
    return 670;
}

//Functions returning double with input params only!

_Export double __cdecl f_double_void() {
    MB("f_double_void()");
    return 3.1;
}

_Export double __cdecl f_double_long(long n) {
    sprintf(sBuf, "f_double_long(%d)", n);
    MB(sBuf);
    return 4.1;
}

_Export double __cdecl f_double_double(double d) {
    sprintf(sBuf, "f_double_double(%.2f)", d);
    MB(sBuf);
    return 5.1;
}

_Export double __cdecl f_double_charptr(char **s) {
    sprintf(sBuf, "f_double_charptr(%s)", s);
    MB(sBuf);
    return 6.1;
}

_Export double __cdecl f_double_long_double_charptr(long n, double d, char **s) {
    sprintf(sBuf, "f_double_long_double_charptr(%d, %.2f, %s)", n, d, s);
    MB(sBuf);
    return 7.1;
}

//Functions with output params only!

_Export void __cdecl f_get_long(long** res) {
    MB("f_get_long()");
    **res = 7;
}

_Export void __cdecl f_get_double(double** res) {
    MB("f_get_double()");
    **res = 3.14;
}

_Export void __cdecl f_get_charptr(char**** res) {
    MB("f_get_charptr ()");
    **res = (char**)malloc(1000);
    strcpy(**res, "got ya");
}

//Mixture

_Export void __cdecl f_all(long nIn, double dIn, char** pIn,
                           long** nOut, double** dOut, char**** pOut) {
    sprintf(sBuf, "f_all(%d, %.2f, %s)", nIn, dIn, pIn);
    MB(sBuf);
    **nOut = 2 ** nIn;
    **dOut = 2 ** dIn;
    **pOut = (char**)malloc(strlen(pIn) ** 2 + 1);
    strcpy(**pOut, pIn);
    strcat(**pOut, pIn);
}

{% endraw %}
```
{: .line-numbers}

