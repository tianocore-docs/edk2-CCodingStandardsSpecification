<!--- @file
  3 Quick Reference

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

# 3 Quick Reference

## 3.1 Naming

* Names must clearly represent the purpose of the named object. See "General
  Naming Rules".

* Do not use names that are very similar to existing concepts, such as 'event'.
  See "General Naming Rules".

* Do not use the names of symbols declared in standard header files as internal
  symbols. See "Function and Data Names".

* Overloading function or type names is not allowed. "Name Space Rules".

* Use the correct opposites when naming. See "Common Opposites in Variable
  Names".

* Use standard abbreviations only. See "Abbreviation Usage".

* Use industry standard acronyms only. See "Acronym Usage".

* Any nonstandard abbreviation or acronym must be defined in the file header of
  any file using the abbreviation or acronym. See "Abbreviation Usage" and
  "Glossary".

* There is no limit to name lengths. A length of 10 to 30 characters is ",
  recommended. See "File Names" & "Identifiers that are always reserved".

* File names must not start with numbers. See "File Names".

* Each include file name must be unique. See "Include Files".

* File, function, variable, enumeration, and data structure elements must have
  names like the following: `EachWordIsDistinctEvenAcronymsLikeAcpi`.
  See "Identifiers".

* Don't capitalize all letters in acronyms. `MyPCIAddress` is hard to read,
  compared to `MyPciAddress`, especially if acronyms are mixed with numbers,
  like `My870PCIBus0BDF`. See "Acronym Usage".

* Acronyms in comments and documentation shall follow English rules and be
  capitalized. See "Acronym Usage".

* Functional macros, `#defines`, and `typedefs` must have names like:
  `EACH_WORD_IS_DISTINCT_EVEN_ACRONYMS_LIKE_ACPI` See "Type and Macro Names".

* Hungarian naming is not allowed. See "Hungarian Prefixes".

* Global data names must be prefaced with a '`g`'. Example: `gMyGuid`. See
  "Global & Module Variables".

* Module global data names must be prefaced with an '`m`'. Example: `mMyGuid`.
  See "Global & Module Variables".

## 3.2 Formatting

### 3.2.1 Formatting: General Rules

* Tab characters are not allowed. See "General Rules".

* All indentation (tabs) is two spaces. See "General Rules".

### 3.2.2 Formatting: Vertical spacing

* Use blank lines and comments to group blocks of related code. See "Vertical
  Spacing".

* Never put more than one statement per line. See "Vertical Spacing".

* Never put the code and conditional on one line. See "Vertical Spacing

* Never put more than one declaration per line. `UINT8 MyData1, MyData2;` is
  illegal. See "Vertical Spacing".

* Always put open braces '`{`' on their own line for functions or multi-line
  predicate expressions. All other uses put the brace following the
  conditional. See "Vertical Spacing".

* Always put close braces '`}`' on their own line, indented to match the first
  line of the construct. Exceptions are `else`, `else if`, and `do-while` code.
  See "Vertical Spacing".

### 3.2.3 Formatting: Horizontal spacing

* Always put space before and after binary operators. See "Horizontal Spacing".

* Never put space between unary operators and the operand. See "Horizontal
  Spacing".

* Always put space after '`,`', or '`;`' if more code follows. See "Horizontal
  Spacing".

* Always put space before a '`(`' except for '`((`'. See "Horizontal Spacing".

* Always put space before a '`{`' if it is not on its own line. See "Horizontal
  Spacing".

* Never put spaces around '`.`' or '`->`' operators. See "Horizontal Spacing".

* Never put a space between array operands and '`[`'. See "Horizontal Spacing".

* Always Line up continued lines with the element being continued. See
  "Horizontal Spacing".

### 3.2.4 Formatting: Predicate Expressions

* Always use parentheses rather than relying on "Horizontal Spacing" (above)
  operator precedence. "Predicate Expressions".

* Booleans do not need to be compared with `TRUE` or `FALSE`. See "Predicate
  Expressions".

* Pointers must be explicitly compared to `NULL`. See "Predicate Expressions".

* Numbers must be explicitly compared to another number. See "Predicate
  Expressions".

## 3.3 Files: General Rules

* Do not use tabs, only use Spaces. "General Rules".

* Unless explicitly stated otherwise, spaces (white space) may be one or more
  space characters long. See "General Rules".

* Files may only contain the ASCII characters 0x0A, 0x0D, and 0x20 through
  0x7E, inclusive. See "General Rules".

* Do not produce lines that exceed 120 columns in your source files. See
  "General Rules".

* New files shall not use `#pragma` except for `#pragma pack(#)`. See "General
  Rules".

  + Ported files may retain pre-existing `#pragma`s. See "General Rules".

  + Ported files may contain `#pragma`s to disable prevalent warning messages.

* All lines must end with CRLF (Carriage Return Line Feed); 0x0D followed by
  0x0A.

* All files must end with CRLF. See "General Rules".

* Every new file must begin with a "File Heading" comment block. See "File
  Heading"

### 3.3.1 Files: Horizontal Spacing

* Always put space before and after binary operators. See "Horizontal Spacing".

* Do not put space between unary operators and their object. See "Horizontal
  Spacing".

* Horizontal spacing for multi-line function calls should line up one or two
  tab stops after the beginning of the function name. See "Horizontal Spacing".

* Always put space after commas or semicolons that separate items. See
  "Horizontal Spacing".

* Always put space before an open parenthesis, except for macro definitions.
  See "Horizontal Spacing".

* Put space before an open brace if it is not on its own line. See "Horizontal
  Spacing".

* Do not put space around the structure member, '`.`', and pointer, '`->`',
  operators. See "Horizontal Spacing".

* Do not put space before the open brackets, '`[`' of array subscripts. See
  "Horizontal Spacing".

* Align a continuation line with the part of the line that it continues. See
  "Horizontal Spacing".

* Use parentheses instead of relying upon knowledge of C precedence ordering.
  See "Horizontal Spacing".

### 3.3.2 Include Files

* Every header file must have a '`#ifndef FILE_NAME_H_`' and '`#endif`' guard
  surrounding all code. See "Include Files".

  + The `#ifndef` must be the first line of code following the file header
    comment.

  + The `#endif` must appear alone on the last line in the file.

* All C include files shall use the same extension and it shall be `.h`. See
  "Include Files".

* Include statements shall not contain absolute paths or paths that contain
  '..'. See "#include"

* Functional macros are discouraged except for includes, debug, CR, and linked
  lists. See "Macros".

* Macros should be defined with the maximum use of parentheses to remove any
  possible ambiguity. See "Macros".

* Include files must contain either public or private data, not both. See
  "Include Files".

* Include files must not contain code generating statements. See "Include
  Files".

* Every parameter must have the proper `IN`, `OUT`, `OPTIONAL`, etc., modifiers.
  See "Function Definition Layout".

* Only use UEFI data types. Use of standard C data types is prohibited. See
  "Common Data Types".

### 3.3.3 Code Files

* Only use UEFI data types. Use of standard C data types is prohibited. See
  "Common Data Types".

* Code files should not contain `#define` and `typedef` statements.

* Do not use inline assembler in the source files. See "General Rules".

* Function definitions, as well as `if`, `for`, `while`, and `switch`
  statements, must follow strict rules. See "Function Definition Layout", "Flow
  Control Statements, and "Introducing Doxygen".

* Enumerated types must end with a maximum element. See "Enumerated Types".

* Enumerated types should begin with a minimum element.

* Structures are always defined with a `typedef` format. See "Structure
  Definitions".

* The open and closing braces of a function definition are in column one and on
  their own lines. See "Function Definition Layout".

### 3.3.4 Code Files: Vertical Spacing

* There shall be only one statement per line. See "Vertical Spacing".

* Open braces, '`{`', shall be on the same line as the closing parenthesis,
  '`)`', of one-line predicate expressions. See "Vertical Spacing".

* Open braces, '`{`', shall be on a line by themselves and aligned with the
  first character of the associated flow control statement when following a
  multi-line predicate expression. See "Vertical Spacing".

* Close braces, '`}`', always go at the beginning of the last line of the body.
  See "Vertical Spacing".

* A close brace may share a line with the `else {`, `else if () {`, and
  do-while constructs. See "Vertical Spacing".

* Each sub-expression of a complex predicate expression must be on a separate
  line. See "Vertical Spacing".

## 3.4 Documentation

### 3.4.1 Documentation: Commenting

* Comments must explain why the code does what it does. See "Comments".

* Every file must have a properly formatted file header. See "File Heading".

* Every function and functional macro must have a correct function header in
  both the source and include files. See "Macros" & "Function Headings".

#### 3.4.1.1 Documentation: Internal comments

* Local comments must use the C++ comment style, '`//`'. See "Internal
  Comments".

* Local comments must have a blank line before the comment block. See "Internal
  Comments".

* Comments must be indented to match the code. See "Internal Comments".

* If a comment applies to more than one block of code, there should be a blank
  line after the comment. See "Internal Comments".

* If a comment applies to a single block of code, there should **not** be a blank
  line separating the comment from the code. See "Internal Comments".

#### 3.4.1.2 Documentation: What not to comment

* **No** comment markers are allowed in code, including:
  + `BUGBUG`
  + Your name
  + Your initials
  + Special markers, such as `FIX_THIS`, `TEST` . See "What NOT to Comment".

* Use your bug tracking system to track bugs instead of markers within the
  code. If you really must mark the code, use Doxygen's `@bug` or `@todo`
  commands. See "What NOT to Comment".

### 3.4.2 Doxygen

* Doxygen comments are used to document global and file-scope elements. See
  "Global Comments".

* C-style comment blocks are of the form:
  ```c
  /** Brief Description.
   *  ... More text ...
  */
  ```

* C++ style comment blocks begin with `///`.

* Comments precede the semantic element they document. See "Special
  Documentation Blocks".

* The special form, `///< ...`, allows documentation to be after the documented
  element. See"Putting Documentation after Members".

* Comment blocks automatically start with a brief description and end at the
  first period. See "Special Documentation Blocks" .

* The most frequently used Doxygen commands are: ( See "Special Commands").

```c
@file [<name>]
@param[in, out] <parameter name> { parameter description }
@retval <return value> { description }
@sa { references }
@test { description of a test case }
```
