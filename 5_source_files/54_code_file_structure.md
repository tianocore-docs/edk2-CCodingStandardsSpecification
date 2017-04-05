<!--- @file
  5.4 Code File Structure

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

## 5.4 Code File Structure

All code generating files use the following general structure. Typically
these are C files with an extension of "`.c`".

```
/** @file
  Definitions of bizarre protocols for something.

  This is a detailed description of the something for which this
  file exists. Something rotates upon the blarvitz allowing
  implementation of bizarre protocols. If the blarvitz is NULL,
  describe what is happening in more detail. If non-NULL, then
  you should probably also explain your rationale.

  Copyright (c) 20XX, Acme Corporation. All rights reserved.<BR>
  This program and the accompanying materials
  are licensed and made available under the terms and conditions of
  the BSD License which accompanies this distribution. The full
  text of the license may be found at
  http://opensource.org/licenses/bsd-license.php

  THE PROGRAM IS DISTRIBUTED UNDER THE BSD LICENSE ON AN "AS IS"
  BASIS, WITHOUT WARRANTIES OR REPRESENTATIONS OF ANY KIND, EITHER
  EXPRESS OR IMPLIED.

  @par Specification Reference:
    - UEFI 2.3, Chapter 9, Device Path Protocol
    - PI 1.1, Chapter 10, Boot Paths
**/
/* Include necessary header files here */
#include <DxeCore.h>
#include <Uefi.h>
#include "SampleThing.h"

/* Define external, global and module variables here */

/* Function Definitions */

/* If this is a protocol definition, the
protocol structure is defined and initialized here.
*/
```

### 5.4.1 Scoping Rules

There are three components of the C language that interact to affect when a
particular variable can be used, or not.

* **Scope:** The context in which an identifier is visible constitutes the scope
  of that identifier..

* **Visibility:** If an identifier can be referenced within a particular scope
  it is said to be visible.

* **Storage Class:** Allocation of storage space is controlled by the storage
  class of an identifier.

#### 5.4.1.1 Scope

Understanding the C scoping rules is critical for good programming. The various
identifier scopes encountered are: file, prototype, function, and block or
local scope.

**File Scope**

Top-level identifiers and preprocessor macros are said to have _file scope_.
Their scope extends from their declaration point to the end of the source
program file. A preprocessor macro can go out-of-scope earlier if a `#undef`
command that cancels its definition is encountered.

**Prototype Scope**

The identifiers making up the formal parameters in function prototypes have
_prototype scope_. Identifiers with prototype scope have scopes extending from
their declaration point to the end of the prototype.

**Function Scope**

Statement labels have _function scope_. Function scope identifiers have scope
which encompasses the entire function body in which they appear. This means
that statement labels can be referenced before they are declared.

**Block (local) Scope**

Formal parameters in function definitions and data defined within compound
statements have block scope. Any group of statements that are encompassed
within a pair of braces, { }, is a compound statement. The body of a function
is also a compound statement. Compound statements can be nested, with each
creating a new scope.

Data declarations may follow the opening brace of a compound statement,
regardless of nesting depth, and before any code generating statements have
been entered. Other than at the outermost block of a function body, this type
of declaration is strongly discouraged.

**********
**Note:** Visual C++ gives all structure declarations File Scope, even though
ISO/IEC 9899 specifies that structure declarations may have Block Scope.
**********

#### 5.4.1.2 Visibility

A declaration of an identifier is _visible_ in some context if a use of the
identifier in that context is associated with that declaration. A declaration
might be visible throughout its scope, but it might also be hidden by other
declarations whose scope and visibility overlap that of the first declaration.

##### 5.4.1.2.1 No two different identifiers in a function may have the same name nor may any of the names in a function be the same as those declared at a global or module level.

* Identifiers with file scope have the outermost scope. Those with block scope
  have the innermost scope. Nesting successive blocks creates more inner scopes.

* Only disallow instances where an outer definition is hidden by a second inner
  definition. This rule is not violated when the first definition is not hidden
  by the second definition.

The following example shows how the scope visibility of identifiers can overlap
and hide each other. Never write code that does this.

```
 1 UINTN MyVar = 7; // File scope
 2
 3 VOID
 4 MyFunction (
 5   OUT UINT32 *MyVar // Function scope
 6   )
 7 {
 8   UINT32 i;
 9
10   for ( i = 0; i < 5; ++i) {
11     UCHAR8 MyVar = i; // Block scope
12     INT16 i = 12;
13
14     MyVar += 'A';
15     process ( MyVar, i);
16   }
17   *MyVar = i;
18 }
19
20 main()
21 {
22   UINT32 George = 4;
23
24   MyFunction ( &George);
25   process ( MyVar, 0);
26 }
27
```

In the above example, there are three declarations of `MyVar`:

* On line 1, `MyVar` is defined with file scope and value 7 This scope extends
  from line 1 through line 26.

* On line 5, `MyVar` is declared as a formal parameter of MyFunction. Its
  context extends from line 5 through the end of the function on line 18.

* On line 11, `MyVar` is declared with block scope. From its declaration point
  on line 11 through the end of the block in which it was declared, this
  declaration of `MyVar` will be in scope. It is initialized to the current
  value of `i`.

To test yourself on your understanding of scope and visibility rules, determine
the value and associated declaration for each use of `MyVar` before reading
further.

The first use of `MyVar` is on line 14 Its associated declaration is on line 11
Each time through the for loop it will have the values 'A', 'B', 'C', and 'D'
in succession.

On line 15, `MyVar` is used again with its associated declaration on line 11
with the same succession of values assigned as on line 14.

`MyVar`, on line 17, associates with the formal parameter declaration on line 5
In this case the value of `i`, which is 5, is stored in the location `MyVar`
points to. The location is established in the call to `MyFunction` on line 24.

The last use of `MyVar` occurs on line 25 This occurrence associates with the
declaration on line 1 and has the value 7.

Things get extremely tricky on line 12 The identifier `i`, which is the control
variable for the enclosing `for` loop, is declared with a different type and
value. It is ambiguous as to which `i` was wanted in line 11. How does this
affect the `for` loop? What will be the value of `i` at lines 15 and 17?

The scope rules tell us the answers, but they still aren't obvious.

* The `i` on line 10 is outside the block, which is the body of the `for` loop.
  It associates with the declaration on line 8, so the `for` loop will continue
  to work as expected.

* On line 11, `MyVar` will be initialized to the current value of `i`. It is
  compiler dependent whether this is the first value of `i`, 0, or the value of
  `i` for each loop.

* Line 12 declares a new variable `i` which is given the value 12 C scoping
  rules state that a scope begins at the declaration point, not at the beginning
  of the block in which the declaration appears. Because of this, the `i` used
  on line 11 is not the same `i` declared here.

* The value of `i` used on line 15 is 12, the value of the associated and
  currently visible identifier with that name.

As you can see, using the same identifier at different scopes can be confusing
at best. All it takes is one mistake and a bug is introduced that is very hard
to locate.

#### 5.4.1.3 Compile-Time Names

So far we have been talking about variable and function identifiers, which have
an existence at run time. However, the scope and visibility rules apply equally
to identifiers applied to objects that don't necessarily exist at run time:
`typedef` names, type tags, enumeration constants, macros, and labels.

Macros and labels follow the rules outlined for them in Section 5.4.1.1 "Scope".
The other compile-time names follow the same scope and visibility rules as any
variable defined at the same location.

### 5.4.2 Storage Class

#### 5.4.2.1 extern

A special case of scope and visibility is the _external_ identifier, also
called an identifier with _external linkage_. All instances of an external
identifier, among all the files making up a C module, are forced to refer to
the same object or function. Each instance of the external identifier must be
declared with the same type in each file or else the result is undefined.

External names are declared using the `extern` keyword. In C89, and earlier
dialects, external identifiers declared at file scope are implicitly extern.
But, not all identifiers declared `extern` were external.

The compilers supported by EDK II follow the C99 specification for `extern`. All
declarations of the external variable must use the `extern` keyword. There must
be a single definition of the external variable which does not use the `extern`
keyword. This definition may also include an initializer.

By convention, external names are declared at the top level of a C program and
therefore have file scope. For EDK II, external names must be declared in a
single header file and must be defined at the top level of a C file as
specified in Section 5.4.1.3 "Compile-Time Names".

Thus, while it might be legal C, do **not** declare external variables anywhere
other than at the top level of a file as specified by this document.

#### 5.4.2.2 Static

An object declared `STATIC` has either file or block scope.

##### 5.4.2.2.1 Do not reuse an object or function identifier with static storage duration.

Throughout the set of source files defined within a single .inf file, do not
reuse an identifier with static storage duration. The compiler may not be
confused by this, but the user may confuse unrelated variables with the same
name.

##### 5.4.2.2.2 Functions should not be declared STATIC.

Some source-level debuggers are unable to resolve static functions. Until it
can be verified that no one is dependent upon a debugger with this limitation,
it is strongly recommended that functions not be declared static.
