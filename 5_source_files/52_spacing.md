<!--- @file
  5.2 Spacing

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

## 5.2 Spacing

Some people claim that spacing is not important and that spacing rules in a
coding style are burdensome and bogus. Review the following example to see why
spacing is important, especially in C:

```c
int i;main(){for(;i["]<i;++i){--i;}"];read('-'-'-',i+++"hello,
world!\n",'/'/'/'));}read(j,i,p){write(j/p+p,i---j,i/i);}
```
_Dishonorable mention, Obfuscated C Code Contest, 1984._

Author requested anonymity.

### 5.2.1 Vertical Spacing

Use blank lines to

* make code more readable
* group logically related sections together.

#### 5.2.1.1 There shall be only one statement on a line

This requirement does not include `for` loops, where the initial, conditional,
and loop statements may go on a single line.

#### 5.2.1.2 The if and while statements are no exception

The conditional and code always go on a separate line.

It should be:

```c
if (MyVar != 0) {
  MyTrueCode ();
}
```

#### 5.2.1.3 An open brace '{' goes on the same line as the closing parenthesis ')' of simple predicate expressions

This requirement includes functions and data. A _simple predicate expression_
is one containing zero or one operator which fits on the same line as the
keyword.

```
while (MyVar != 0) {
```

#### 5.2.1.4 A close brace '}' always goes at the beginning of the last line of the body

Indent the brace to match the first line of the construct.

```c
while (MyVar != 0) {
  MyTrueCode ();
}
```

#### 5.2.1.5 A close brace may share a line with the else {, else if () {, and do-while constructs

```c
} else {
} else if (foo) {
} while (bar);
```

#### 5.2.1.6 Each sub-expression of a complex predicate expression must be on a separate line

Predicate expressions containing multiple operators with sub-expressions joined
by && or || must have each sub-expression on a separate line. The opening brace,
'`{`' of the body shall be on a line by itself and aligned in the starting
column of the associated keyword.

```c
while ( ( Code == MEETS_STANDARD)
  && ( Code == FUNCTIONAL))
{
  ShipIt();
}
```

### 5.2.2 Horizontal Spacing

#### 5.2.2.1 Unless explicitly stated otherwise, space may be one or more spaces long

#### 5.2.2.2 Always put space before and after binary operators.

This space makes both operands much easier to read.

```c
if (MyVar != 0) {
  MyTrueCode ();
}
```

#### 5.2.2.3 Do not put space between unary operators and their object

```
If ((--MyInteger) > 0) {
```

#### 5.2.2.4 Subsequent lines of multi-line function calls should line up two spaces from the beginning of the function name

If a function call or function like macro invocation is broken up into multiple
lines, then:

* One argument per line, including the first argument on its own line.
* Indent each argument 2 spaces from the start of the function name. If a
  function is called through a structure or union member, of type
  pointer-to-function, then indent each argument 2 spaces from the start of the
  member name.
* Align the close parenthesis with the start of the last argument

```c
CopyMem (
  Destination,
  Source,
  SIZE_4KB
  );

Status = gBS->AllocatePool (
                EfiBootServicesData,
                sizeof (DRIVER_NAME_INSTANCE),
                &PrivateData
                );

DEBUG ((
  DEBUG_INFO,
  "The addresses of the 4 buffers are %p, %p, %p, and %p\n",
  Buffer1,
  Buffer2,
  Buffer3,
  Buffer4
  ));
```

#### 5.2.2.5 Always put space after commas or semicolons that separate items

This punctuation is not necessary if no code or comments follow the comma or
semicolon.

```c
EfiLibAllocateCopyPool (Size, DevicePath);
for (Size = 0; FileName[Size] != 0; Size++) {...
```

#### 5.2.2.6 Always put space before an open parenthesis

The only exception is macro definitions.

```c
if (...
while (...
EfiLibAllocateCopyPool (...
```

#### 5.2.2.7 Put a space before an open brace if it is not on its own line

```
if () {
while () {
```

#### 5.2.2.8 Do not put spaces around structure member and pointer operators

```c
Data.Index
Pointer->Index = *Ptr;
```

#### 5.2.2.9 Do not put spaces before open brackets of array subscripts

```
Array[(Max + Min) / 2]
```

#### 5.2.2.10 Use extra parentheses rather than depending on in-depth knowledge of the order of precedence of C

(The order of precedence should be the compiler's job, not yours.)

Consider the following expression:

```
8 | 8 == 8
```

On first glance, one might think that the expression would evaluate to `TRUE`.
This is not the case. The bitwise OR operator, '`|`', has lower precedence than
the equality operator, '`==`'. This results in the expression being evaluated as
if one had entered:
```
8 | ( 8 == 8 )
```

This evaluates to the value 9.

#### 5.2.2.11 Align a continuation line with the part of the line that it continues.

```c
Value = (GetData (BubbaBaes + BUBBA_HIGH_DATA) << 8) |
         GetData (BubbaBaes + BUBBA_LOW_DATA);
```

### 5.2.3 File Heading

#### 5.2.3.1 Every new file shall begin with a file header comment block

This block shall begin on the first line of the file. This is a Doxygen file
descriptor comment block, so line 1 of the file will be:

```
/** @file
```

And the comment will end with:

```
**/
```

The File Heading comment block is comprised of the following sections: File
Description, Copyright, License, and the optional Specification Reference and
Glossary sections.

```c
/** @file
  File Description.

  Copyright
  License

  Specification Reference

  Glossary Section
**/
```

The following example begins each body line with a tab (two spaces). This is
the preferred indentation, but two tabs (four spaces) is also acceptable.

#### Example

```c
/** @file
  Brief description of the file’s purpose.

  Detailed description of the file’s contents and other useful
  information for a person viewing the file for the first time.

  Copyright (C) --20XX, Acme Corporation. All rights reserved.<BR>
  SPDX-License-Identifier: BSD-2-Clause-Patent

  @par Revision Reference:
    - PI Version 1.0

  @par Glossary:
    - IETF - Internet Engineering Task Force
    - NASA - National Aeronautics and Space Administration
**/
```

#### 5.2.3.2 File Description

The file description consists of a brief, one sentence, description of the
file's purpose as well as a detailed description of the files purpose and
content.

The brief description begins on the second line of the comment block and
terminates at the first period. Do not include text indicating that the file is
a header, include, declaration, or definition file as this is intrinsically
obvious.

The detailed description follows the brief description, separated by a blank
line. All subsequent text and blank lines are part of the detailed description
until terminated by a Doxygen command or the end of the comment.

**********
**Note:** The Copyright Notice and License comprise the last paragraph of the
detailed file description. They are described separately, below.
**********

The file description describes the purpose of the file (why the file exists), a
general description of what it contains, and the relationship of the file to a
particular module or modules, if any.

#### 5.2.3.3 Copyright

The first line of the last paragraph of the file description is made up of the
copyright notice. The copyright notice must consist of the following text with
the `FIRST` and `LAST` symbols replaced with the year the file was created and
the year the file was last edited, respectively.

```
Copyright (C) FIRST - LAST, Acme Corporation. All rights reserved.<BR>
```

A file that has been created but not edited in subsequent years would have a
copyright notice with a single date, such as:

```
Copyright (C) 2007, Acme Corporation. All rights reserved.<BR>
```

If this file is subsequently edited, the copyright notice would be updated as
follows.

```
Copyright (C) 2007 - 2014, Acme Corporation. All rights reserved.<BR>
```

The `FIRST - LAST` format for the copyright date, as described above, is the
only format allowed. Do not use a comma separated list or keep updating a
single date. The space surrounding the hyphen, '`-`', between the `FIRST` and
`LAST` dates is optional.

The `<BR>` at the end of the line is required. Doxygen uses XML for its
internal format, so repeated spaces and new lines are treated as a single
space. The `<BR>` will force Doxygen to start the following text, the license
notice, on a new line.

#### 5.2.3.4 License

EDK II code files may contain one of several different licenses, depending upon
the location and content of the file. The correct license will be determined by
the project leader at the time the file is created. In most cases, the license
will be the same as for other files in the module or package.

The preferred license for EDK II is the "BSD+Patent" license.  The license for
a file is provided in the file header using an SPDX identifier.  The following
shows the SPDX identifier for the "BSD+Patent" license.

```
SPDX-License-Identifier: BSD-2-Clause-Patent
```

The license follows the copyright notice.  The license is separated from the
Specification Reference, if present, by a single blank line.

#### 5.2.3.5 Specification Reference

If the file declares or implements something described in one or more UEFI or
Industry Standard specifications, it must include a specification reference
section in the file description comment block. The section begins with a
Doxygen directive:

```
@par Revision Reference:
```

Each specification is listed on a separate line. All specification references
must use the list format. An indented line beginning with a dash character,
'-', indicates list format.

```
@par Revision Reference:
  - UEFI Version 2.2
  - PI Version 1.0
```

#### 5.2.3.6 Glossary

If the file uses a non-standard Abbreviation or Acronym, it must include a
Glossary section in the file description comment block. The section begins with
a Doxygen directive:

```
@par Glossary:
```

Each Glossary definition is listed on a separate line. All Glossary definitions
must use the list format.

```
@par Glossary:
  - IETF - the Internet Engineering Task Force
  - NASA - National Aeronautics and Space Administration
```
