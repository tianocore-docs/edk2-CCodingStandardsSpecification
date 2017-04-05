<!--- @file
  6.7 How Doxygen Works

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

## 6.7 How Doxygen Works

Doxygen understands the `#include` and `#define` preprocessor directives as
well as the syntax of C and C++. Thus, Doxygen can generate documentation using
just the existing syntactic elements of the source files, or one can supplement
the syntactic documentation using Section 6.8 "Special Documentation Blocks".
These special documentation blocks are just C or C++ comments with one or more
special tags added.

For structures, unions, functions, and global data, you have two documentation
options:

* Place a special documentation block in front of the declaration or
  definition. For enum, structure, and union members, you are also allowed to
  place documentation directly after a member. See Section 6.8
  "Special Documentation Blocks", to learn more about special documentation
  blocks.

* Place a special documentation block somewhere else (another file or location)
  and put a structural command in the documentation block. A structural
  command links a documentation block to a certain entity that can be
  documented (e.g. a union, structure, function, or file).

The text inside a special documentation block is parsed before it is written to
the output files. During parsing, the following steps take place:

1. The special commands inside the documentation block are executed.

2. If a line starts with some whitespace followed by one or more asterisks (*)
   and then optionally more whitespace, then all leading whitespace and
   asterisks are removed.

3. All resulting blank lines are treated as paragraph separators. This saves
   you from placing new-paragraph commands yourself in order to make the
   generated documentation readable.

4. Links to members are automatically created when certain patterns are found
   in the text. These patterns include: URLs and email addresses, names of
   documented classes and files, function and variable names, typedef, enum
   types, enum values, and defines.

5. HTML tags that are in the documentation are interpreted and converted to the
   proper equivalents for the selected output type.
