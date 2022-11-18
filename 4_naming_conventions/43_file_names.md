<!--- @file
  4.3 File Names

  Copyright (c) 2006-2022, Intel Corporation. All rights reserved.<BR>
  Copyright (C) 2022 Advanced Micro Devices, Inc. All rights reserved.<BR>

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

## 4.3 File Names

### 4.3.1 There is no limit to file name lengths.

Do not assume that file names must be 8.3 compatible. Be reasonable though. Let
the file names be as long as necessary, but no longer. Some operating systems
limit file names to 32 characters.

### 4.3.2 Spaces in file and directory names are NOT permitted.

Allowing spaces would cause problems with certain versions of existing industry
tools and does not provide additional clarity.

### 4.3.3 Never start file names with numbers.

Most source control systems will not be able to handle file names that start
with numbers.

### 4.3.4 Non-standard characters shall not occur in file names.

All file names within an EDK II source tree must comply with the following
regular expression:

```
[A-Za-z][_A-Za-z0-9-]*[A-Za-z0-9]+
```

That is, a letter followed by zero, or more, letters, underscores, dashes, or
digits followed by a period followed by one or more letters or digits.

### 4.3.5 File naming guidelines for modules

Below sections are the file naming guidelines for EDK II meta files and source files. The
guidelines are not just considering the the uniformity of file naming, but it also provides
the flexibility of file name construction for the scenario of different EDK II module
designs; such as the support for multiple processor architectures and vendors. It may require the
further discussions between EDK II maintainers and contributors in order to determine the best
naming of the EDK II module file.

#### 4.3.5.1 EDK II meta files within a package

```
<PackageName>Pkg.dec
<PackageName>Pkg.dsc

   <PackageName> REQUIRED  *
```

#### 4.3.5.2 EDK II INF file within a Module instance
* If the implementation is for all CPU architectures, specific CPU architectures, CPU vendors or the implementation is shared by certain CPU archs:

```
<Feature><Phase>[<CpuArch>][<Vendor>].inf

   <Feature>      REQUIRED    *
   <Phase>        REQUIRED    Base, Sec, Pei, Dxe, DxeRuntime, Mm, StandaloneMm,
                              Smm, Uefi.
   <CpuArch>      OPTIONAL    The <CpuArch> is represented with a BNF,
                              <arch> ::='Ia32' | 'X64' | 'Arm' | 'AArch64' | 'RiscV64' |
                                        'LoongArch64' | 'Ebc'
                              <CpuArch> ::= <arch>[<arch>]*
                              
                              Example: Ia32X64Arm or RiscV64LoongArch64
   <Vendor>       OPTIONAL    *

Example:
   - SmbiosDxe.inf
   - CpuIo2Dxe.inf
   - CpuIo2DxeAmd.inf
   - CpuIo2DxeIa32X64.inf
   - CpuIo2DxeIa32X64Intel.inf
```

* If the implementation does not have any shared code between phases (e.g., Pcd/Dxe):

```
[<Feature>][<CpuArch>][<Vendor>].inf

   <Feature>      OPTIONAL    *
   <CpuArch>      OPTIONAL    The <CpuArch> is represented with a BNF,
                              <arch> ::='Ia32' | 'X64' | 'Arm' | 'AArch64' | 'RiscV64' |
                                        'LoongArch64' | 'Ebc'
                              <CpuArch> ::= <arch>[<arch>]*
                              
                              Example: Ia32X64Arm or RiscV64LoongArch64
   <Vendor>       OPTIONAL    *
Example:
   Pcd.inf
```

#### 4.3.5.3 EDK II INF file within a Library instance

```
<Phase>[<CpuArch>][<Vendor>]<LibraryClassName>[<Dependency>].inf
   <Phase>              REQUIRED     Base, Sec, Pei, Dxe, DxeRuntime, Mm,
                                     StandaloneMm, Smm, Uefi.
   <CpuArch>            OPTIONAL     The <CpuArch> is represented with a BNF,
                                     <arch> ::='Ia32' | 'X64' | 'Arm' | 'AArch64' | 'RiscV64' |
                                               'LoongArch64' | 'Ebc'
                                     <CpuArch> ::= <arch>[<arch>]*
                              
                                     Example: Ia32X64Arm or RiscV64LoongArch64
   <Vendor>             OPTIONAL     *
   <LibraryClassName>   REQUIRED     *
   <Dependency>         OPTIONAL     * (Typically name of PPI, Protocol, LibraryClass
                                       that the implementation is layered on top of)

Example:
   - SmmAmdSmmCpuFeaturesLib.inf
   - SmmIa32X64SmmCpuFeaturesLib.inf
```

#### 4.3.5.4 EDK II source files within a Library/Module instance

In generally, the file name is constructed as below:

```
[<CpuArch>][<Vendor>]<FileName>.*

   <CpuArch>   OPTIONAL   The <CpuArch> is represented with a BNF,
                          <arch> ::='Ia32' | 'X64' | 'Arm' | 'AArch64' | 'RiscV64' |
                                    'LoongArch64' | 'Ebc'
                          <CpuArch> ::= <arch>[<arch>]*

                          Example: Ia32X64Arm or RiscV64LoongArch64
   <Vendor>    OPTIONAL   *
   <FileName>  REQUIRED   Refer to 4.3.1 to 4.3.4 sections for the file
                          naming format.

Example:
   SmmCpuFeatureLib.c
   SmmCpuFeatureLibCommon.c
   Ia32X64SmmCpuFeaturesLib.c
   Ia32X64IntelSmmCpuFeaturesLib.c
   AmdSmmCpuFeaturesLib.c
```