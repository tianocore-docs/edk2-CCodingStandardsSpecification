<!--- @file
  4 Naming Conventions

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

# 4 Naming Conventions

## 4.1 General Naming Rules

**Use good naming practice when declaring variable names.**

Studies show that programs with names averaging 10 to 16 characters are the
easiest to debug. The name length is just a guideline_; the most important
thing is that the name conveys a clear meaning of what it represents_.

**Do not overload commonly used terms.**

For example, EFI has an event model, so don't call some abstraction that you
define an Event. People will get confused. Make sure someone reading the code
can tell what you are talking about.

**Each word or concept must start with a capital letter and be followed by
lower-case letters.**

The intent is for names to be consistent and easily readable. Each word in a
compound name should be visually distinct.

### 4.1.1 Identifiers that are always reserved

**Identifiers beginning with an underscore are always reserved**

Define them only in the special ways allowed elsewhere in this document.

**Identifiers that are defined in the Standard C and POSIX libraries are always
reserved.**

This includes macros, typedefs, variables, and functions, whether with external
linkage or file scope. The only exception is with modules that are mutually
exclusive with these libraries. These reserved identifiers are listed in
"Reserved Identifiers" and reserved keywords are listed in "Reserved Keywords".

### 4.1.2 Common Opposites in Variable Names

Use the correct opposites when declaring names.

###### Table 1 Common Opposites

|                       |                 |                  |
| --------------------- | --------------- | ---------------- |
| add / remove          | begin / end     | create / destroy |
| increment / decrement | first / last    | get / release    |
| lock / unlock         | put / get       | up / down        |
| old / new             | min / max       | next / previous  |
| source / destination  | open / close    | show / hide      |
|                       | source / target | start / stop     |

### 4.1.3 Abbreviation Usage

#### 4.1.3.1 The use of abbreviations shall be regulated.

This document describes a common set of abbreviations that can be freely used.
If you must make up abbreviations, remember the name is most important to the
reader of the code, not the writer.

#### 4.1.3.2 New abbreviations must be documented in the header of each using file.

Any abbreviation used, which is not documented in this specification, or in the
_UEFI Specification_ shall be placed into a Glossary section of the File header
as specified in "File Heading".

Do not define a new abbreviation to replace an abbreviation that is already
defined in this document. For example, do not define No to mean Number, because
Num is the supported abbreviation.

"EFI Supported Abbreviations" below lists the abbreviations that are
standardized by this document and do not require a defining comment.

###### Table 2 EFI Supported Abbreviations

| Abbreviation | Description             |
| ------------ | ----------------------- |
| Ptr          | Pointer                 |
| Str          | Unicode string          |
| Ascii        | ASCII string            |
| Len          | Length                  |
| Arg          | Argument                |
| Max          | Maximum                 |
| Min          | Minimum                 |
| Char         | Character               |
| Num          | Number                  |
| Temp         | Temporary               |
| Src          | Source                  |
| Dst          | Destination             |
| BS           | EFI Boot Services Table |
| RT           | EFI Runtime Table       |
| ST           | EFI System Table        |
| Tpl          | EFI Task Priority Level |

#### 4.1.3.3 Powers of 2 and 10

You are encouraged to use the IEC international abbreviations for powers of 2
(KiB for 2^10, MiB for 2^20, GiB for 2^30, etc.) rather than the old KB, MB,
and GB, which IEC now reserves for powers of 10 (10^3, 10^6, 10^9). Given that
many readers of the code may not have made the conversion to add the 'i', do
not use KB, MB, and GB for powers of 10 Instead, use e.g. "2*10^6 bytes"
instead of 2MB to avoid confusion. Note that GiB is derived from the G in
'Giga', the 'i' in binary, and the B in 'Byte'.

### 4.1.4 Acronym Usage

#### 4.1.4.1 The use of acronyms shall be limited.

Please remember the golden rule: Code for the person who will have to read and
maintain your code. Making up your own vocabulary to describe your module can
lead to lots of confusion.

#### 4.1.4.2 Created Acronyms must be fully defined.

If you must create acronyms, they must be fully defined in the documentation

##### 4.1.4.2.1 Translation tables are required for each module using a created acronym

Each module that uses the acronym must contain a translation table comment in
the file header. This definition is required so that others can understand your
names and comments.

#### 4.1.4.3 Industry-Standard Acronyms are allowed

It's okay to use acronyms for industry standards.

Acronyms such as Pci, Acpi, Smbios, Isa, (capitalized per the variable naming
convention) are all legal to use without defining their meaning.

If you reference an industry standard acronym, the file header must define to
which version of the specification the code is written. Thus, a PCI resource
manager would state that it was coded to follow the PCI 2.2 Specification and
which optional features it included support for.

#### 4.1.4.4 Capitalize Acronyms in comments and documentation to match their industry standard use.

For example, use "PCI" in comments and documentation, and "Pci" for functions,
files, etc.

The table below lists the acronyms that are considered integral to the EDK II
vernacular, and may be used without defining their meaning in a comment.

###### Table 3 EFI Supported Acronyms

| Acronyms | In an Identifier | Description                                        |
| -------- | ---------------- | -------------------------------------------------- |
| ACPI     | Acpi             | Advanced Configuration and Power Interface         |
| AGP      | Agp              | Accelerated Graphics Port                          |
| ANSI     | Ansi             | American National Standards Institute              |
| ASCII    | Ascii            | American Standard Code for Information Interchange |
| ATA      | Ata              | Advanced Technology Attachment                     |
| ATAPI    | Atapi            | Advanced Technology Attachment Packet Interface    |
| BFD      | Bfd              | Boot Flash Device                                  |
| BIOS     | Bios             | Basic Input/Output System                          |
| BIS      | Bis              | Boot Integrity Services                            |
| CMOS     | Cmos             | Complementary metal oxide semiconductor            |
| CPU      | Cpu              | Central processing unit                            |
| CRC      | Crc              | Cyclic Redundancy Check                            |
| DMA      | Dma              | Direct Memory Access                               |
| DXE      | Dxe              | Driver Execution Environment                       |
| EFI      | Efi              | Extensible Firmware Interface                      |
| FD       | Fd               | Flash Device                                       |
| FIFO     | Fifo             | First In First Out                                 |
| FV       | Fv               | Firmware Volume                                    |
| GUID     | Guid             | Globally Unique Identifier                         |
| IEC      | Iec              | International Electrotechnical Commission          |
| ISA      | Isa              | Industry Standard Architecture                     |
| ISO      | Iso              | International Standards Organization               |
| NVRAM    | Nvram            | Nonvolatile Random Access Memory                   |
| PCI      | Pci              | Peripheral Component Interconnect                  |
| PEI      | Pei              | Pre-EFI Initialization environment                 |
| RAM      | Ram              | Random Access Memory                               |
| ROM      | Rom              | Read-Only Memory                                   |
| SRAM     | Sram             | Static Random Access Memory                        |
| TPL      | Tpl              | Task Priority Level                                |
| UEFI     | Uefi             | Unified Extensible Firmware Interface              |
| UNDI     | Undi             | Universal Network Driver Interface                 |
| USB      | Usb              | Universal Serial Bus                               |
| VGA      | Vga              | Video graphics array                               |
