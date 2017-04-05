<!--- @file
  4.3 Identifiers

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

## 4.3 Identifiers

### 4.3.1 Identifiers shall not rely on the significance of more than 31 characters.

Identifiers (variable names, labels, structure tags, derived macro names, etc.)
may be an arbitrary length. The ISO standard only guarantees that language
processors only pay attention to the first 31 symbols when comparing
identifiers. Note that the same ISO standard requires that external labels
(those visible to the linker) be unique in their first six characters. Since it
has been confirmed that 31 character / case significance is supported by EDK II
supported tool chains, there is no requirement to ensure uniqueness of
externals within the first 6 characters.

### 4.3.2 Always make identifier names that are visually distinguishable.

While not as big an issue as it has been in the past, when choosing labels
ensure that the label is unlikely to be confused with other labels used in the
file. Ensure that long label names vary by more than one or two characters.
Ensure that labels don't vary between zero and oh (0 and O), one and ell (1 and
l). Some also consider 2 and Z, and 5 and S to be similar.

### 4.3.3 Hungarian Prefixes

#### 4.3.3.1 Use of Hungarian notation is not allowed

This set of detailed guidelines for naming variables and routines is a
convention widely used with the C programming language, especially in
Microsoft* Windows* programming. An example of a non-compliant variable named
with the Hungarian conventions follows:

```
bmRequestType;  // Byte mask, First byte in the USB message header
pachInsert;     // A pointer to an array of characters to insert.
```

Global data and module data shall be prefixed with 'g' or 'm', respectively.
Pointer variables may optionally be prefixed with 'p'. These are the only
exceptions to the prohibition against Hungarian notation.

#### 4.3.3.2 Any variable with file scope, or better, shall be prefixed by an 'm' or 'g'

There are no exceptions to this rule. The '`m`' prefix identifies a variable
with module scope, while a '`g`' prefix identifies a global variable.

```
gThisIsAGlobalVariableName
mThisIsAModuleVariableName
```

#### 4.3.3.3 Pointer variables may optionally be prefixed with a 'p'

Time has shown that pass-by-value vs. pass-by-reference errors are
significantly reduced with only the introduction of a '`p`' prefix for pointer
variables.

#### 4.3.3.4 Reasons use of Hungarian prefixes not allowed

The abstraction of abstract data types is ignored. Instead, base types based on
programminglanguage integers or long integers are abstracted. Thus, the names
are focused on data types instead of the object-oriented abstraction that they
represent. This focus is of little value and forces manual type checking that
can be accomplished easily by the compiler with warnings promoted to errors.

Hungarian notation combines data meaning with data representation. If you
change a data type you have to rename the variable. There is no mechanism to
ensure that the names are accurate.

Studies have shown that Hungarian notation tends to encourage lazy variable
names. It's common to focus on the Hungarian prefix without putting effort into
a descriptive name.

### 4.3.4 Function and Data Names

#### 4.3.4.1 Identifiers shall contain mixed upper- and lower-case text.

Use of all upper- or all lower-case is very difficult to read because compound
words cannot be clearly separated.

#### 4.3.4.2 The names of newly created global entities (such as structures, macros, and defines) shall not use an `EFI_` prefix.

From now on, the use of `DXE_` and `PEI_` prefixes shall be reserved for DXE and
PEI drivers, respectively. If a structure happens to apply equally to PEI and
DXE, it should use the prefix `DXE_`. If a structure is local to a particular
module only, no special prefix is required.

#### 4.3.4.3 Acronyms are not capitalized in Function and Data Names.

When all letters in an acronym are capitalized, it makes the prior and
subsequent words visually difficult to distinguish.

```
ThisIsAnExampleOfWhatToDoForPci
```

#### 4.3.4.4 Never use C keywords or the names of symbols declared in the standard header files as internal symbols.

When you need to use the name of an existing library function for a
user-defined function, each use of the user-defined function must be paired
with a corresponding comment. The ISO standard does not, however, guarantee
that the user-defined function will take priority over the library function.

##### 4.3.4.4.1 List of the C-reserved keywords.

In principle, the ISO standard, reserves all names beginning with underscore +
capital letter, or with underscore + underscore. External symbols names shall
not begin with an underscore.

###### Table 4 Reserved Keywords

|              |                |            |            |            |
| ------------ | -------------- | ---------- | ---------- | ---------- |
| auto         | break          | case       | char       | const      |
| continue     | default        | do         | double[^a] | else       |
| enum         | extern         | float[^a]  | for        | goto       |
| if           | int            | long       | register   | return     |
| short        | signed         | sizeof     | static     | struct     |
| switch       | typedef        | union      | unsigned   | void       |
| volatile     | while          | inline     | restrict   | wchar_t    |
| bool         | true           | false      | NULL       | _Bool[^b]  |
| _Complex[^b] | _Imaginary[^b] | and[^c]    | and_eq[^c] | bitand[^c] |
| bitor[^c]    | compl[^c]      | not[^c]    | not_eq[^c] | or[^c]     |
| or_eq[^c]    | xor[^c]        | xor_eq[^c] |            |            |

[^a]: Floating point operations are not recommended in UEFI firmware.

[^b]: These keywords are specific to C99 and are not reserved in C++.

[^c]: Macros defined in header iso646.h. These identifiers are reserved in C++ and are defined as part of the C Standard Library.


In addition to those listed, the identifiers asm and fortran are common
language extensions and should also be treated as reserved.

### 4.3.5 Type and Macro Names

#### 4.3.5.1 Use all capital letters for both #define and typedef declarations.

This clearly differentiates static declarations from dynamic data types.

#### 4.3.5.2 Each word of a concept shall be separated by an underscore character.

The underscore effectively separates the words, making names more readable.

#### 4.3.5.3 The use of the "_t" suffix, designating a type, is not allowed.

```
typedef UINT32 THIS_IS_AN_EXAMPLE_OF_WHAT_TO_DO_FOR_PCI;
```

#### 4.3.5.4 The names of guard macros shall end with an underscore character.

The guard macro, used in the `#ifndef` at the start of an include file, uses a
postfix underscore character '`_`', in its name in order to prevent collision
with other names that follow the naming convention. This may not be sufficient
for header files that don't have a unique name. In that case, additional text
may have to be added to the macro name in order to make it unique. This may not
be required if the header files are mutually exclusive.

```c
#ifndef FILE_NAME_H_
#define FILE_NAME_H_
...
#if (A_NUMBER > 72)
...
#else // NOT (A_NUMBER > 72)
...
#endif // (A_NUMBER > 72)
...
#endif /* FILE_NAME_H_ */
```

#### 4.3.5.5 The #else and #endif clauses of conditional compilation blocks shall be commented to identify their context.

If a conditional compilation construct spans more than seven lines, a comment
shall be added to the construct's `#else` and `#endif` clauses identifying the
block the clause is associated with. This is illustrated in the preceding code
example. The comment shall be on the same line as the `#else` or `#endif`
clause.
