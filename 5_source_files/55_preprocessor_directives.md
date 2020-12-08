<!--- @file
  5.5 Preprocessor Directives

  Copyright (c) 2006-2017, Intel Corporation. All rights reserved.<BR>

  Redistribution and use in source (original document form) and 'compiled'
  forms (converted to PDF, epub, HTML and other formats) with or without
  modification, are permitted provided that the following conditions are met:

  1) Redistributions of source code (original document form) must retain the
     above copyright notice, this list of conditions and the following
     disclaimer as the first lines of this file unmodified.

  2) Redistributions in compiled form (transformed to other DTDs, converted to
     PDF, epub, HTML and other formats) must reproduce the above copyright
     notice, this list of conditions and the following disclaimer in the
     documentation and/or other materials provided with the distribution.

  THIS DOCUMENTATION IS PROVIDED BY TIANOCORE PROJECT "AS IS" AND ANY EXPRESS OR
  IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF
  MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO
  EVENT SHALL TIANOCORE PROJECT  BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL,
  SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO,
  PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS;
  OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY,
  WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR
  OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS DOCUMENTATION, EVEN IF
  ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

-->

## 5.5 Preprocessor Directives

### 5.5.1 #include

#### 5.5.1.1 Use the proper file delimiters when including files

Use either double quotes or angle brackets. A file name delimited by angle
brackets, `<FileName.h>`, indicates that the compiler should search the default
include paths and those specified by '`-I`' directives on the compiler command
line (System Include Files). If one uses double quotes to delimit the file
name, "`FileName.h`", the compiler will first search the directory containing
the file being compiled before then searching the System include paths.

The general rule to be derived from this is that one should use double quotes
to include files in the same directory as, or a subdirectory of, the file being
compiled, and angle brackets for all other include files.

```c
#include <Uefi.h> /* System include file. */
#include "SampleThing.h" /* In same directory as the C file. */
```

#### 5.5.1.2 Include file paths shall be relative and shall not contain ".." elements.

All include paths must be relative to either the current .c file, or a
predefined include directory.

### 5.5.2 Macros

#### 5.5.2.1 Functional macros are generally discouraged.

Parameterized macros are difficult to debug, have difficult syntax, do not
encourage strong commenting, and generally negatively impact maintainability
and understandability of code. Macros are appropriate for some concepts, such
as containment records and include path abstraction.

#### 5.5.2.2 Macros follow the standard data naming conventions used by typedef and #define.

The main reason for making a macro different from a function is the difference
in the order of precedence that can occur between poorly constructed macros and
functions.

#### 5.5.2.3 Overusing parentheses is strongly encouraged.

An order-of-precedence bug in a macro is very hard to debug. The following are
examples of macro construction:

```
#define BAD_MACRO(a, b) a * b
#define GOOD_MACRO(a, b) ((a) * (b))
```

The following examples should explain the difference between `BAD_MACRO ()` and
`GOOD_MACRO ()`:

* `BAD_MACRO (10, 2)` and `GOOD_MACRO (10, 2)` both evaluate to 20.

* `BAD_MACRO (7 + 3, 2)` returns 13 = 7 + (3 * 2).

* `GOOD_MACRO (7 + 3, 2)` returns 20.

Also, consider the following expression:

```
8 | 8 == 8
```

On first glance, one might think that the expression would evaluate to `TRUE`.
This is not the case. The bitwise OR operator, '`|`', has lower precedence than
the equality operator, '`==`'. This results in the expression being evaluated as
if one had entered:

```
8 | (8 == 8)
```

This evaluates to the value 9 The desired result of `TRUE`, (1), can be achieved
by specifying the expression as:

```
((8 | 8) == 8)
```

#### 5.5.2.4 Macros must have comment blocks like functions.

Macros can be very difficult to debug, so explicit descriptions of the input,
output, and behavior are required. This is true whether it is a parameterized
or a simple substitution macro.

#### 5.5.2.5 Parameterized macro definitions shall not have a space between the name and the '(.'

Failure to do this will cause the build to break.

```
#define GOOD_MACRO(a, b) ((a) * (b))
```

This is because the compiler has no way to differentiate between

```
#define SIMPLE_MACRO (a) (TXT)
```

which substitutes all subsequent occurrences of SIMPLE_MACRO with (a) (TXT), and

```
#define PARAM_MACRO(a) (a) (TXT)
```

which defines a parameterized macro.

#### 5.5.2.6 When using a macro, there must be a space between the name and the '(' to comply with function calling conventions.

Failure to separate macro names from parameters negatively impacts readability
and consistency with other coding style rules.

```
GOOD_MACRO (7 + 3, 2)
```

#### 5.5.2.7 Single-line Functions

Most uses of parameterized macros can be replaced by one or two line functions.
The compilers will almost always in-line the function resulting in the same
effect as the parameterized macro. An additional benefit of single-line
functions is the type checking the compiler can now provide.
