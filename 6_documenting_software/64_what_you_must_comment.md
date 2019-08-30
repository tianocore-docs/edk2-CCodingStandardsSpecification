<!--- @file
  6.4 What You Must Comment

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

## 6.4 What You Must Comment

### 6.4.1 Comment function declarations if public, or implementations if private and not declared.

You must describe the purpose of the function and any side effects. Also
describe the purpose or meaning of each parameter and return value.

### 6.4.2 Comment complicated, tricky, or sensitive pieces of code.

What the code is doing must be made clear. Making the code cleaner is often
better than adding more comments.

### 6.4.3 Comment higher-level concepts in the code.

Focus on the why and not the how.

### 6.4.4 Comment data structure declarations and #define statements.

The include files should be sufficient to understand what data or code are for.
It should not be necessary to search for all references to something to
understand its purpose and use. If more than one instance of a structure or
union is instantiated, comment each one as to its intended purpose. It should
be clear from these comments why there are multiple instances and how each
instance differs.

### 6.4.5 File comments should include the version number of the industry standard to which you are coding.

When possible, you should also list the requirements that are satisfied by the
code.

### 6.4.6 Comment spurious variable assignments.

A compiler or static code analyzer may warn that an object with automatic or
allocated storage duration is read without having been initialized, while
visual inspection reveals that this is impossible.

In order to suppress such a warning (which is emitted due to invalid data flow
analysis), developers explicitly assign the affected object the value to which
the same object would be initialized automatically, had the object static
storage duration, and no initializer. (The value assigned could be arbitrary;
the above-mentioned value is chosen for stylistic reasons.) For example:

```c
UINTN LocalIntegerVariable;
VOID  *LocalPointerVariable;

LocalIntegerVariable = 0;
LocalPointerVariable = NULL;
```

This kind of assignment is difficult to distinguish from assignments where the
initial value of an object is meaningful, and is consumed by other code without
an intervening assignment. Therefore, each such assignment must be documented,
as follows:

```c
UINTN LocalIntegerVariable;
VOID  *LocalPointerVariable;

//
// set LocalIntegerVariable to suppress incorrect compiler/analyzer warnings
//
LocalIntegerVariable = 0;
//
// set LocalPointerVariable to suppress incorrect compiler/analyzer warnings
//
LocalPointerVariable = NULL;
```
