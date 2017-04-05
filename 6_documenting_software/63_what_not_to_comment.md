<!--- @file
  6.3 What NOT to Comment

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

## 6.3 What NOT to Comment

### 6.3.1 Do not repeat the code or explain it in a comment.

Comments should clarify the intent of the code or explain higher-level
concepts. The code itself should be clear and self-documenting.

There is a famously bad comment:

```
i = i + 1; // Add one to i
```

This comment provides no information beyond what is already obvious from
reading the code. There are even worse ways to do it, such as:

```
/**********************************
* *
* Add one to i *
* *
**********************************/

      i=i+1;

```


### 6.3.2 Do not leave markers in the code.

Don’t leave flags, such as your name, in the code. They may have meaning to you
but they do not to other people or projects. Don’t make fancy patterns in your
comments so you can search for them later. Always consider that the code and
comments represent both you and your company and will very likely be publicly
available. The presence of flags, like `BugBug`, or `ToDo` statements indicating
that comments should be added, reflect poorly upon the programmer.

### 6.3.3 Sections of code shall not be “commented out”.

Where sections of source code must not be compiled, use conditional compilation
(such as `#if` or `#ifdef` constructs with a descriptive comment) to meet this
requirement. C does not support nested comments, and the application of start
and end comment markers to meet the requirement of source code that must not be
compiled is a dangerous practice. This is because comments already existing in
the section of code would change the outcome.

### 6.3.4 Do not comment out, or otherwise disable, previous revisions of the code.

Rely on your source control system to retain history, not your code.

### 6.3.5 Do not use the character sequence “/*” within a comment.

C does not support the nesting of comments, despite the existence of such
support (as a language extension) within some compilers. Comment start with `/*`
and end when the first `*/` is encountered.
