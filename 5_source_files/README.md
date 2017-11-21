<!--- @file
  5 Source Files

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

# 5 Source Files

## 5.1 General Rules

### 5.1.1 Lines shall be 120 columns, or fewer

Preferably, limit line lengths to 80 columns or fewer. When this doesn't leave
sufficient space for a good postfix style comment, extend the line to a total
of 120 columns. Having some level of uniformity in the expected width of the
source is useful for viewing and printing the code.

### 5.1.2 Do not use tab characters

Tabs shall be set in all editors to expand to two spaces. All indentation is on
two space boundaries. There are no exceptions to this rule! This rule makes
code look the same in all editors.

### 5.1.3 Files may only contain the ASCII characters 0x0A, 0x0D, and 0x20 through 0x7E

Files should be saved using either ASCII or UTF8 encoding.

### 5.1.4 Only escape sequences defined in the ISO C standard shall be used in string literals.

Implementing hexadecimal escape sequences, '\x20' for example, is prohibited
because they vary from compiler to compiler.

The ISO standard defines octal escape sequences: '\102', for example. Because
of the similarity to decimal values, and octal having fallen into disuse, use
of this construct is prohibited. The only exception to this rule is '\0'.

Other than '\0', the only permissible escape sequences are:

###### Table 5 Permissible Escape Sequences (ISO/IEC 9899:1990 6.1.3.4)

|      |                                        |
| ---- | -------------------------------------- |
| `\a` | Alert: Visual or audible alert         |
| `\b` | Backspace: Move to previous position   |
| `\f` | Form Feed: Move to next logical page   |
| `\n` | New Line: Move to start of next line   |
| `\r` | Carriage Return: Move to start of line |
| `\t` | Horiz. Tab: Move to next tab position  |
| `\v` | Vert. Tab: Move to next Vert. Tab pos. |
| `\’` | Single Quote                           |
| `\”` | Double Quote                           |
| `\0` | NUL character                          |
| `\\` | Single Backslash                       |

### 5.1.5 Octal constants (Base 8) shall not be used.

The C language specification defines numbers whose first digit is zero as
octal, so 010 is decimal 8. The use of octal has declined considerably since C
was first defined, but this construct remains for backwards compatibility. Its
use is prohibited. In particular, do not be tempted to use the zero prefix in
tables of numbers to ensure visual alignment:

```c
Address[0] = 00130;  // Decimal 88
Address[1] = 01450;  // Decimal 808
Address[3] = 81200;  // Decimal 81200
```

### 5.1.6 Only use CRLF (Carriage Return Line Feed) line endings.

Use Windows, or MSDOS, style line endings. Do NOT use Unix / Linux / MacOS /
OS-X file formats.

### 5.1.7 All files must end with CRLF

The last two characters in any source file within EDK II must be a CRLF: 0x0D
followed by 0x0A.

### 5.1.8 Trigraphs shall not be used

Trigraphs are a construct to allow character representations that do not
support all ASCII characters to enter the equivalent of the ASCII character.
Trigraphs are three characters long (hence the "tri"). The first two characters
are "??" while the third character disambiguates the trigraph. Technically
therefore, a[5] could be written a??(5??). Trigraphs have proven both
confusing and unnecessary and are prohibited.

### 5.1.9 In-line assembler shall not be used

There are really no reasons for in-line assembler to be used in EDK II code.
The only exceptions in this case are largely associated with the lowest level
Architectural Protocols. Using in-line assembly language deviates from the
Scope rules defined in Section 1.3 "Scope", because it is an extension to
standard C.

### 5.1.10 Do not use #pragma, except for #pragma pack (#).

The only other exception for this would be in the `ProcessorBind.h` file.
