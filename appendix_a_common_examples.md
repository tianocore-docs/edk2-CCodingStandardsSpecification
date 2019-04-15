<!--- @file
  APPENDIX A Common Examples

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

# APPENDIX A Common Examples

#### File Heading

```c
/** @file
  Brief description of file’s purpose.

  Detailed description of file’s purpose.

  Copyright (c) 2006 - 2014, Acme Corporation. All rights reserved.<BR>
  SPDX-License-Identifier: BSD-2-Clause-Patent

  @par Specification Reference:
  - UEFI 2.3, Chapter 9, Device Path Protocol
  - PI 1.1, Chapter 10, Boot Paths
**/
#ifndef FOO_BAR_H_
#define FOO_BAR_H_

// Body of the file goes here

#endif // FOO_BAR_H_
```

#### Functioon Declarations

```c
/** Brief description of this function's purpose.

  Follow it immediately with the detailed description.

  @param[in]       Arg1  Description of Arg1.
  @param[in]       Arg2  Description of Arg2 This is complicated and requires
                         multiple lines to describe.
  @param[out]      Arg3  Description of Arg3.
  @param[in, out]  Arg4  Description of Arg4.

  @retval  VAL_ONE  Description of what VAL_ONE signifies.
  @retval  OTHER    This is the only other return value. If there were other
                    return values, they would be listed.

**/
EFI_STATUS
EFIAPI
FooBar (
  IN     UINTN  Arg1,
  IN     UINTN  Arg2, OPTIONAL
     OUT UINTN  *Arg3,
  IN OUT UINTN  *Arg4
  );
```

#### Type Declarations

```c
/// Brief description of this enum.
/// Detailed description if justified.
typedef enum {
  EnumMenberOne,  ///< First member description.
  EnumMemberTwo,  ///< Second member description.
  EnumMemberMax   ///< Number of members in this enum.
} ENUMERATE_TYPE;

/// Structure without forward reference.
typedef struct {
  UINT32                   Signature;  ///< Signature description.
  EFI_HANDLE               Handle;     ///< Handle description.
  EFI_PROD_PROT1_PROTOCOL  ProdProt1;  ///< ProdProt1 description.
  EFI_PROD_PROT2_PROTOCOL  ProdProt2;  ///< ProdProt2 description.
} DRIVER_NAME_INSTANCE;

/// Self referential Structure.
typedef struct EFI_CPU_IO_PROTO {
  struct EFI_CPU_IO_PROTO     *Mem;
  EFI_CPU_IO_PROTOCOL_ACCESS  Io;
} EFI_CPU_IO_PROTOCOL;

/// Forward reference
typedef struct StructTag MyStruct;

/// Forward reference target
struct StructTag {
  INT32 First;
  INT32 Second;
};
```

#### Function Calling

```c
Status = TestString ();
Status = TestString (String, Index + 3, &Value);
Status = TestString (
           String,
           Index + 3,
           &Value
           );
```

#### Control Statements

```c
if (Test && !Test2) {
  // This is an example comment to explain why this behavior
  // is appropriate.
  IamTheCode ();
} else if (Test2) {
  // This is an example comment to explain why this behavior
  // is appropriate.
  IamTheCode ();
} else {
  // This is an example comment to explain why this behavior
  // is appropriate.
  IamTheCode ();
}

while (TRUE) {
  IamTheCode ();
}

do {
  IamTheCode ();
} while (TRUE);

for (Index = 0; Index < MAX_INDEX; Index++) {
  IamTheCode (Index);
}

switch (Variable) {
case 1:
  IamTheCode ();
  break;

case 2:
  IamTheCode ();
  break;

default:
  IamTheCode ();
  break;
};
```
