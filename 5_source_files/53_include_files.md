<!--- @file
  5.3 Include Files

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

## 5.3 Include Files

### 5.3.1 All C include file names shall contain only one extension and it must be .h.

Using only one extension dramatically simplifies build issues and standardizes
naming.

### 5.3.2 Every include file shall have a unique name.

The name of all include files, within the EDK II code base, must be unique. The
uniqueness test applies to the entire path used in the #include directive. For
example:

```
#include <Peach/Pit.h>
#include "Olive/Pit.h"
#include <MoneyPit.h>
#include "OpenPit.h"
```

These are unique, even if the file name itself is not, as long as the preceding
path component is included.

To see why this is necessary, consider a package, `FruitPkg`, that has the
following in its DEC file:

```ini
[Includes]
  Include
  Include/Olive
  Include/Peach
```

Both the `Include/Olive` and `Include/Peach` directories contain a file `Pit.h`.
It then becomes ambiguous which file is being referenced if one encounters
`#include <Pit.h>` in a source file. This ambiguity would be compounded if
another package, also dependent upon `FruitPkg`, contained a `Pit.h` file in its
`Include` directory.

Existing automatically generated include files, such as `AutoGen.h`, are
exempted from this rule. It is not mandatory to rename pre-existing include
files.

Unique file names may also be formed by appending or prepending a short
character sequence, such as the module or package name in which the file
resides, or an abbreviation of one of these, to the file name.

```
PeachPit.h OlivePit.h MoneyPit.h PitBoss.h
```

### 5.3.3 Include files shall not consist mainly of include directives.

This type of omnibus header file can significantly increase the time required
to rebuild a project. If any of the included files changes, every file that
includes the omnibus file will have to be recompiled; even if that particular
file did not use the changed header file.

### 5.3.4 Include files may include only those headers that it directly depends upon.

This maintains proper dependency relationships between the files and allows the
header file to be used without prior knowledge of its dependencies.

### 5.3.5 All include file contents must be protected by a #include guard.

Also known as a "macro guard", use #include guards to avoid multiple inclusions
when dealing with the include directive. Adding `#include` guards to a header
file makes that file idempotent.

```c
#ifndef FILE_NAME_H_
#define FILE_NAME_H_
...
#endif // FILE_NAME_H_
```

Avoid duplicating the guard macro name in different header files. Including a
duplicate guard macro name prevents the symbols in the other from being
defined. Names starting with one or two underscores, such as
`_MACRO_GUARD_FILE_NAME_H_`, must not be used. They are reserved for compiler
implementation.

With modern programming practices, particularly include files including other
include files, it is almost impossible to avoid including the same file more
than once. This can only slow down the processing time and may cause difficult
to diagnose issues. To avoid this, the use of _macro guards_ is required in all
include files to protect against inadvertent multiple inclusion.

* The `#ifndef` shall be on the first line following the file header comment.
  This location ensures that all code is contained.

* The `#endif` shall appear as the last line in the file.  The `#endif` is
  followed by a comment consisting solely of the guard token. The line shall end
  with a carriage return (new line) as the last thing in the file, thus ensuring
  that all code is contained.

### 5.3.6 Include files shall contain only public or only private data.

Include files must not contain both types of information. Examples of public
include files would be protocol definitions or industry standard specifications
(EFI, SAL, ACPI, SMBIOS, etc.). Private data would include functions and
internal data structure declarations used only within a single module.

### 5.3.7 Include files shall not generate code or define data variables.

Including code or defining variables can result in issues that are very
difficult to debug.

The sample below shows the suggested order of declarations in an include file.
Not all types of declarations are present in every file.

```c
/** @file
  Public declarations of bizarre protocols for something.

  This is a detailed description of the something for which this
  file exists. Something rotates upon the blarvitz allowing
  implementation of bizarre protocols. If the blarvitz is NULL,
  describe what is happening in more detail. If non-null, then
  you should probably also explain your rationale.

  Copyright (c) 20XX, Acme Corporation. All rights reserved.<BR>
  This program and the accompanying materials
  are licensed and made available under the terms and conditions of
  the BSD License which accompanies this distribution. The full
  text of the license may be found at
  http://opensource.org/licenses/bsd-license.

  THE PROGRAM IS DISTRIBUTED UNDER THE BSD LICENSE ON AN "AS IS"
  BASIS, WITHOUT WARRANTIES OR REPRESENTATIONS OF ANY KIND, EITHER
  EXPRESS OR IMPLIED.

  @par Specification Reference:
    - UEFI 2.3, Chapter 9, Device Path Protocol
    - PI 1.1, Chapter 10, Boot Paths
**/
#ifndef SAMPLE_THING_H_
#define SAMPLE_THING_H_

/* Include directives for dependent header files */

/* Simple defines of such items as status codes and macros */

/* Type definitions */

/* Function prototype declarations */

/* Protocol declarations */

#endif /* SAMPLE_THING_H_ */
```
