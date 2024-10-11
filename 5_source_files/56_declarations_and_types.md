<!--- @file
  5.6 Declarations and Types

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

## 5.6 Declarations and Types

### 5.6.1 Common Data Types

#### 5.6.1.1 The UEFI Specification defines a set of common data types that must be used to ensure portability between different compilers and processor architectures.

Any abstract type that is defined must be constructed from other abstract types
or from common EFI data types.

#### 5.6.1.2 The use of int, unsigned, char, void, long is a violation of the coding convention.

The corresponding EFI types must be used instead.

"EFI Data Types" below contains the common data types that are referenced in
the interface definitions defined by this specification. Per the _UEFI
Specification_, version 2.3.1:

"Unless otherwise specified, all data types are naturally aligned. Structures
are aligned on boundaries equal to the largest internal datum of the structure,
and internal data is implicitly padded to achieve natural alignment."

###### Table 6 EFI Data Types (slightly modified from UEFI 2.3.1)

| Mnemonic     |  Description                                                                                                                                                           |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `BOOLEAN`    | Logical Boolean. 1-byte value containing a 0 for `False` or a 1 for `True`. Other values are undefined.                                                                |
| `INTN`       | Signed value of native width. (4 bytes on IA-32, 8 bytes on X64, and 8 bytes on the Intel(R) Itanium(R) processor family)                                              |
| `UINTN`      | Unsigned value of native width. (4 bytes on IA-32, 8 bytes on X64, and 8 bytes on the Intel(R) Itanium(R) processor family)                                            |
| `INT8`       | 1-byte signed value.                                                                                                                                                   |
| `UINT8`      | 1-byte unsigned value.                                                                                                                                                 |
| `INT16`      | 2-byte signed value.                                                                                                                                                   |
| `UINT16`     | 2-byte unsigned value.                                                                                                                                                 |
| `INT32`      | 4-byte signed value.                                                                                                                                                   |
| `UINT32`     | 4-byte unsigned value.                                                                                                                                                 |
| `INT64`      | 8-byte signed value.                                                                                                                                                   |
| `UINT64`     | 8-byte unsigned value.                                                                                                                                                 |
| `CHAR8`      | 1-byte character.                                                                                                                                                      |
| `CHAR16`     | 2-byte character. Unless otherwise specified, all strings are stored in the UTF-16, 2-byte, encoding format as defined by the Unicode 2.1 and ISO/IEC 10646 standards. |
| `VOID`       | Undeclared type.                                                                                                                                                       |
| `EFI_GUID`   | 128-bit buffer containing a unique identifier value. Unless otherwise specified, aligned on a 64bit boundary.                                                          |
| `EFI_STATUS` | Status code. Type `UINTN`.                                                                                                                                             |
| `EFI_HANDLE` | Handle to a device driver. Type `VOID *`.                                                                                                                              |
| `EFI_EVENT`  | Handle to an event structure. Type `VOID *`.                                                                                                                           |
| `EFI_LBA`    | Logical block address. Type `UINT64`.                                                                                                                                  |
| `EFI_TPL`    | Task priority level. Type `UINTN`.                                                                                                                                     |

"Modifiers for Common EFI Data Types" defines modifiers that are used in
function and data declarations. The `IN`, `OUT`, `OPTIONAL`, and `UNALIGNED`
modifiers are used only to qualify arguments to a function. They should never
appear in a data type declaration. The `EFIAPI` modifier is used to ensure the
correct calling convention is used between different modules that are not linked
together. Use this modifier at the entry of drivers, events, and member
functions of protocols.

The `EFIAPI` modifier must be used for all UEFI defined API functions, as well
as for any function that takes a variable number of arguments. All protocol
functions as well as public functions exposed by drivers must also be declared
`EFIAPI`. This establishes a common calling convention for functions that could
be referenced by other code that has potentially been built using a different
compiler, with a different native calling convention.

###### Table 7 Modifiers for Common EFI Data Types (reference the UEFI Specification and Beyond Bios)

| Mnemonic    | Description                                                                                                                                                                                     |
| ----------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `IN`        | Datum is passed to the function.                                                                                                                                                                |
| `OUT`       | Datum is returned from the function.                                                                                                                                                            |
| `OPTIONAL`  | Datum that is passed to the function is optional, and a `NULL` may be passed if the value is not supplied.                                                                                      |
| `UNALIGNED` | Datum is byte packed and is not naturally aligned.                                                                                                                                              |
| `VOLATILE`  | Declares a variable to be volatile and thus exempt from optimization to remove redundant or unneeded accesses. Any variable that represents a hardware device should be declared as `VOLATILE`. |
| `CONST`     | Declares a variable to be of type `const`. This type is a hint to the compiler to enable optimization and stronger type checking at compile time.                                               |
| `EFIAPI`    | Defines the calling convention for EFI interfaces. All EFI intrinsic services and any member function of a protocol must use this modifier on the function definition.                          |


### 5.6.2 Constants

#### 5.6.2.1 EFI Constants

"EFI Constants" below lists the EFI constants that should be used to represent
certain concepts.

###### Table 8 EFI Constants

| Mnemonic | Description                                         |
| -------- | --------------------------------------------------- |
| `TRUE`   | One = ( 1 < 2 ) == 1; Any non-zero value is `TRUE`. |
| `FALSE`  | Zero = ( 2 < 1 ) == 0                               |
| `NULL`   | `VOID` pointer to zero. ((void*)0)                  |

#### 5.6.2.2 Enumerated Types

* The elements of the enumerated type must follow the data and function naming
  convention.

  The `enum` shall be declared as a `typedef` with the name of the `typedef`
  following the type and macro naming conventions in` "Type and Macro Names".

* The last element of the enum should be a maximum member element.

  This convention allows for bounds checking on an `enum` to support debugging
  and sanity checking the value that is assigned to an `enum`. It is also
  recommended that the `enum` members be named carefully, such that their names
  would not tend to collide with other variable or function names.

  ```c
  typedef enum {
    EnumMemberOne,  ///< Automatically initialized to zero.
    EnumMemberTwo,  ///< This has the value 1
    EnumMemberMax   ///< The value 2 here indicates there are two elements.
  } ENUMERATED_TYPE;
  ```

  This obviously will not work if values are explicitly assigned out-of-sequence
  or are duplicated.

* All constants that will be used "as is" should be declared as enums.

  An enum does not cause code to be generated until the enum is used, whereas a
  const int will cause space for the int to be allocated as well as the code
  generated whenever the int is used. The use of enums allows type checking to
  be performed, while the use of macros does not`.`

#### 5.6.2.3 Macro Constants

Constants that will be used to construct other values should be declared as
macros.  These include bit field definitions and masks.

#### 5.6.2.4 Pointers and Constants

There are three different ways pointers and constants can interact:

* Pointer to Constant:

  ```
  CONST UINTN * PointerToConst;
  ```

  `PointerToConst` is a variable pointer to a constant `UINTN`.

* Constant pointer to variable:

  ```
  UINTN * CONST ConstPointer;
  ```

  `ConstPointer` is a constant pointer to a variable `UINTN`.

* Constant pointer to constant:

  ```
  CONST UINTN * CONST ConstPointerToConst;
  ```

  `ConstPointerToConst` is a constant pointer to a constant `UINTN`.

### 5.6.3 Structure Declaration

Structures shall be declared as a `typedef` with one of two different styles
depending on the use of the structure. If the structure is not
self-referential, or there is no forward reference to it, the structure may be
defined anonymously; see Section "Structure Reference".

This anonymous definition is valid because we typedef the structure in the
definition.

* The structure name and typedef name shall follow the type and macro naming
  conventions in "Type and Macro Names" on page 24`

* Structure instances: Variables, parameters, members, etc., must follow the
  file, function, and data naming conventions in "Identifiers" through
  "Name Space Rules".

* Structures are always defined in a `typedef struct name {...} type;` format.

The "name" tag is allowed only if the structure is self-referential or the
target of a forward reference.

#### 5.6.3.1 Structures shall not be directly declared.

The following are not allowed:

```
struct name {...}; // OK if object of forward reference
struct {...} variable; // Never OK
struct name {...} variable; // Never OK
```

#### 5.6.3.2 Structure Declaration with Forward Reference or Self-Reference

```c
/// Sample forward declaration of a structure.
typedef struct EFI_STRUCT_NAME EFI_STRUCT_NAME;

/// Sample self-referential structure declaration.
typedef struct EFI_STRUCTURE_NAME {
  ...
  struct EFI_STRUCTURE_NAME *StructPointer;  ///< Sample self reference
} EFI_STRUCT_NAME;
```

#### 5.6.3.3 Structure Declaration without Forward Reference

```c
/** Brief description of sample structure declaration.
  *
  * Detailed description of purpose and use of this structure.
**/
typedef struct {
  Atype  memberOne;  ///< Briefly describe memberOne
  ...
  Ztype  memberN;    ///< Briefly describe memberN
} EFI_STRUCTURE_NAME;
```

#### 5.6.3.4 Bit Fields

A member of a structure or union may be declared to consist of a specified
number of bits (including a sign bit, if any). That member is referred to as a
bit-field. Bit fields differ from other members in that:

* Bit fields may only be of type `INT32`, `signed INT32`, `UINT32`, or a
  typedef name defined as one of the three `INT32` variants.

* It is compiler defined whether `INT32` is signed or unsigned.

* The order of allocation of bit-fields within a storage unit is compiler
  defined.

* The alignment of the addressable storage unit is unspecified.

* A bit-field may not extend from one storage unit into another.

A bit-field with only a colon and a width (no declarator), indicates an unnamed
bit-field. Unnamed bit-fields are useful for padding to conform to externally
imposed layouts.

Specifying a bit-field with a width of 0 (zero) indicates that no further
bit-fields are to be packed into the unit in which the previous bit-field, if
any, was placed.

##### 5.6.3.4.1 Visual C++ Specific

* The alignment requirement for each non-bit-field member is the same as the
  largest alignment requirement of the members. Thus, every member will have
  the same alignment.

* A "plain" `int` bit-field is treated as a `signed int` bit field.

* Bit fields are allocated within a storage unit from least-significant to
  most-significant bit.

##### 5.6.3.4.2 GCC Specific

* The alignment requirement for non-bit-field members of structures is
  determined by the target ABI.

* By default, a "plain" `int` bit-field is treated as a `signed int`, but this
  may be changed by the '-funsigned-bitfields' option.

* The order of allocation of bit-fields within a unit is determined by the
  target ABI.
