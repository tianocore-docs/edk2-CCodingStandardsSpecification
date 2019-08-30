<!--- @file
  6.2 Comments

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

## 6.2 Comments

Commenting has always been a delicate matter, requiring taste and judgment. One
should assume that others reading the code know the implementation language.
Code that is clear, using good type and variable names, should be
self-explanatory - at a micro level. Comments should explain the
less-than-obvious aspects of the code, at a macro level.

**********
**Note:** The comments need to explain why things were done and the big picture
of how something works and the ways in which the various pieces relate to each
other.
**********

By definition, misleading comments can cause confusion. When you modify code,
you should always check the comments to ensure that they accurately document
the modified code. Comments are not checked by the compiler, and are therefore
not guaranteed to be correct. Comments are even more of a risk following code
modification.

Write your comments assuming that they are going to be read by someone with
minimal familiarity with the code. Clarity is important, but one should also
strive for terse and concise comments. One should be able to see both the
comment, and the code being commented on, on the same screen.

### 6.2.1 Only use C style, "/*", comments for multi-line comments and on the same line as pre-processor directives.

Compile can vary in their support for use of `//` in preprocessor directives
(e.g. `#define`). Note that the mixing of `/* ... */` and `//` is not handled
consistently. This goes beyond style issues; various (pre C99) compilers may
not behave the same.

### 6.2.2 Avoid banners or other decoration around blocks of comments.

Banners can be useful to highlight logical divisions within a file; such as
before vital sections. This type of usage should be minimized.

### 6.2.3 Do not include jokes or obtuse references in comments.

```
"Out of cheese error! Redo from start."
```
