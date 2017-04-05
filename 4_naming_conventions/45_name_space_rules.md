<!--- @file
  4.5 Name Space Rules

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

## 4.5 Name Space Rules

ISO C defines several name spaces (see ISO/IEC 9899:1994 6.1.2.3). The same
name could be used in a separate name space for a completely different item.

Name spaces are defined as:

* label names
* tags of structures, unions and enumerators
* Members of structures or unions
* All other identifiers.

**********
**Note:** Name space and scope are not synonymous. Name space rules do not
apply to scope. Scope is described in "Scoping Rules".
**********

### 4.5.1 Names shall be used consistently within the same type.

For example, structure tags may only be reused as structure types, and union
tags may be reused only for union types.

```c
typedef struct MyStruct {
  int  one;
  int  two;
  int  three;
} MY_STRUCT;
```

Because of the similarity of `MyStruct` to `MY_STRUCT`, they may only be used
to refer to the same structure type.

### 4.5.2 No identifier in one name space may be reused as an identifier in another name space

Exceptions are structure member and union member names.

```c
typedef struct StructOne {
  INT32             one;
  INT16             two;
  struct StructOne  *MySelf;
} STRUCT_ONE;

typedef struct StructTwo {
  INT16             one;
  INT8              *two;
  struct StructTwo  *MySelf;
} STRUCT_TWO;

typedef struct {
  STRUCT_ONE  *StructOne;     // NOT ALLOWED
  STRUCT_TWO  *StructTwoPtr;  // ALLOWED, it is unique
} BAD_STRUCT;
```

### 4.5.3 A typedef name shall be a unique identifier.

The name that appears at the end of a typedef (`STRUCT_ONE` and `STRUCT_TWO` in
the example in Section 4.5.2) is known as a _typedef name_. Because of ambiguity
in the C specifications, and to avoid confusion, and once a typedef name is used
in a structure declaration, it may not be declared elsewhere

**********
**Note:** Including the declaration in a header file that is then included in a
number of files is not a violation of this rule.
**********

### 4.5.4 A tag name shall be unique.

The name after the `struct` in structure definitions (`StructOne` and
`StructTwo` in the example in 4.5.2) is known as a _structure tag_ or simply a
_tag_. To avoid confusion, once a tag is used for declaring a structure it
shall not be declared elsewhere.

**********
**Note:** Including a header file that contains a structure definition is not a
violation of this rule.
**********

### 4.5.5 Prefix module-scope identifiers for cleaner namespaces.

The use of prefixes is not an absolute requirement, but has been shown as a
successful method of avoiding namespace pollution and makes it easier to meet
other naming requirements. A useful prefix is the module's name. For example,
the UEFI Shell uses the prefix "Shell" for its identifiers.

```
SHELL_FREE_NON_NULL (Buffer);
ShellCommandLibConstructor (ImageHandle, SystemTable);
```
