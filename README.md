# BlitzMaxNG Grammar Definition
```
; Status: 23/JUL/2021, Incomplete
; Please refer to ABNF definitions in RFC 5234

; Define Tokens identified by Lexer
; Status: Incomplete
%1:SUPERSTRICT,%2:STRICT,%3:FRAMEWORK,%4:INCLUDE...

; PROGRAMS, MODULES AND BLOCKS

program = [strictmode] [framework] \*import

strictmode = "superstrict" / "strict" CRLF
framework = "framework" CRLF
import = "import" string "." string CRLF
include = "include" string CRLF

function = "function" string [ ":" vartype ]
           "(" params ")" block
           "endfunction" / ("end" "function)
method = "method" string [ ":" vartype ]
         "(" params ")" 
         block
         "endmethod" / ("end" "method")

type = "type" string [ "extends" string ]
       \*(field / const / global / "private" / "public" / method / function )
       "endtype" / ("end" "type")

vartype = "int" / "string" / "double" / "float"

comment = "'" \*( WSP / string ) CRLF
remark = "rem" \*( WSP / string / CRLF ) "endrem" / ( "end" "rem")
CRLF = %d13.10

local = "local" vardecl \*[ "," vardecl ]
field = "field" vardecl \*[ "," vardecl ]
global = "global" vardecl \*[ "," vardecl ]

vardecl = string ":" vartype [ "=" expression ]



```
