# Lexical Elements

## Comments

```go
// Single line comment
/* 
    Multiple line comment
*/
```

## Semicolons

Semicolons mark the end of statements, but the may be omitted at end of line:

```go
var a int = 1; var b int = 2 // useful for merged lines but discouraged
var c int = 3                // can be omitted outherwise
```

## Keywords

The following are Go reserved keywords:

```go
break        default      func         interface    select
case         defer        go           map          struct
chan         else         goto         package      switch
const        fallthrough  if           range        type
continue     for          import       return       var
```

## Operators & Punctuations

The following are all operator combinations:

```go
+    &     +=    &=     &&    ==    !=    (    )
-    |     -=    |=     ||    <     <=    [    ]
*    ^     *=    ^=     <-    >     >=    {    }
/    <<    /=    <<=    ++    =     :=    ,    ;
%    >>    %=    >>=    --    !     ...   .    :
     &^          &^=
```

## Integer Literals

Integer literals represent an _integer constant_.

```go
// zero
0

// decimal
42
1234567890

// start with 0 for octal
0600

// start with 0x or 0X for hexadecimal       
0xBadFace1
0XBadFace2
```

## Floating-point Literals

Floating-point literals represent a _floating-point constant_.

```go
// fractional
0.      // = 0
.25     // = 0.25
72.40
072.40  // 72.40
2.71828

// exponential - the following are all = 100
     1e2;     1E2
    1e+2;    1E+2
   100e0;   100E0
  100e+0;  100E+0
  100e-0;  100E-0
10000e-2; 1000E-2

// exponential - the following are all 100
   .1e+3;    .1E+3
    .1e3;     .1E3
    1.e2;     1.E2
   1.e+2;    1.E+2
  100.e0;   100.E0
 100.e+0;  100.E+0
 100.e-0;  100.E-0
1000.e-2; 1000.E-2

// fractional exponential - the following are all 12.34
 1234.e-2;  1234.e-2
  1234e-2;   1234e-2
 12.34e-0;  12.34e-0
  12.34e0;   12.34e0
 12.34e+0;  12.34e+0
 .1234e+2;  .1234e+2
0.1234e+2; 0.1234e+2
```

## Imaginary Literals

Imaginary literals represent a imaginary part of a _complex constant_.

```go
// decimal
0i
42i
011i // = 11i

// exponential
0e0i; 0E0i
5e1i; 5E1i

// fractional     
.0i; 0.i; 0.0i
1.2i
0.21i
12.i

// fractional exponential
.0e0i; .0E0i; 0.e0i; 0.E0i; 0.0e0i; 0.0E0i
.0e+0i; .0E+0i; 0.e+0i; 0.E+0i; 0.0e+0i; 0.0E+0i
.0e-0i; .0E-0i; 0.e-0i; 0.E-0i; 0.0e-0i; 0.0E-0i
```

## Rune Literals

Rune literals represents a _rune constant_. These \_characters \_are **Unicode code point** enclosed in single quotes `'`.

```go
// valid examples
'a'; 'ä'; '本';         // can be unicode literals
'\000'; '\007'; '\377' // unicode octal value
'\x07'; '\xff'         // unicode hexadecimal value
'\u12e4'; '\U00101234' // unicode hexadecimal value

// the following are special characters
'\a'   // U+0007 alert or bell
'\b'   // U+0008 backspace
'\f'   // U+000C form feed
'\n'   // U+000A line feed or newline
'\r'   // U+000D carriage return
'\t'   // U+0009 horizontal tab
'\v'   // U+000b vertical tab
'\\'   // U+005c backslash
'\''   // U+0027 single quote  (valid escape only within rune literals)
'\"'   // U+0022 double quote  (valid escape only within string literals)

// invalid examples
'\'          // rune literal containing single quote character
'aa'         // illegal: too many characters
'\xa'        // illegal: too few hexadecimal digits
'\0'         // illegal: too few octal digits
'\uDFFF'     // illegal: surrogate half
'\U00110000' // illegal: invalid Unicode code point
'\y'         // illegal: invalid escape character
```

## String Literals

String literals represents a \_string constant. \_These are concatenated sequence of runes/characters.

```go
// raw string literals are character sequences between back quotes `string`
`abc`      // same as "abc"
`\nhello
world\n`   // same as "\\nhello\nworld\\n" - no escape sequences work in raw strings literals 
           // and new lines are accepted


// interpreted string literals are character sequences between double quotes "string"
"\n"
"\""                 // same as `"`
"Hello, world!\n"
"日本語"
"\u65e5本\U00008a9e"
"\xff\u00FF"
"\uD800"             // illegal: surrogate half
"\U00110000"         // illegal: invalid Unicode code point

// all the above are the same unicode string
"日本語"                                 // UTF-8 input text
`日本語`                                 // UTF-8 input text as a raw literal
"\u65e5\u672c\u8a9e"                    // the explicit Unicode code points
"\U000065e5\U0000672c\U00008a9e"        // the explicit Unicode code points
"\xe6\x97\xa5\xe6\x9c\xac\xe8\xaa\x9e"  // the explicit UTF-8 bytes
```



