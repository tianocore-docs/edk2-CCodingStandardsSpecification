<!--- @file
  4.2 Directory Names

  Copyright (C) 2022 Advanced Micro Devices, Inc. All rights reserved.<BR>
  Copyright (c) 2022, Intel Corporation. All rights reserved.<BR>

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

## 4.2 Directory Names
Below sections are the directory naming guidelines for EDK II modules. The guidelines are not
just considering the uniformity of directory naming, but they also provide the flexibility of
directory name construction for the scenario of different EDK II module designs; such as the
support for multiple processor architectures and vendors. It may require further discussions
between EDK II maintainers and contributors in order to determine the best naming of the EDK II
module directory.

#### 4.2.1 EDKII package directory

```
<PackageName>Pkg

   <PackageName> REQUIRED  *
```

#### 4.2.2 EDKII Module directory

* The guideline below is applied to all CPU architectures support, specific CPU architecture and vendors support, or the implementation is shared by certain CPU archs:

```
<Feature><Phase>[<CpuArch>[<Vendor>]]
  or
<Feature><Phase>[/<CpuArch>[/<Vendor>]]

   <Feature>      REQUIRED    *
   <Phase>        REQUIRED    Base, Sec, Pei, Dxe, DxeRuntime, Mm, StandaloneMm, Smm,
                              Uefi.
   <CpuArch>      OPTIONAL    The <CpuArch> is represented with a BNF,
                              <arch> ::='Ia32' | 'X64' | 'Arm' | 'AArch64' | 'RiscV64' |
                                        'LoongArch64' | 'Ebc'   
                              <CpuArch> ::= <arch>[<arch>]*
                              
                              Example: Ia32X64Arm or RiscV64LoongArch64
   <Vendor>       OPTIONAL    *

Example:
   - SmbiosDxe/
   - CpuDxe/                    # First implementation of CpuDxe.
   - CpuDxeIa32X64Amd/          # Ia32 and X64 AMD specific implementation.
   - CpuDxe/RiscV64/            # RiscV64 specific implementation.
           /                    # Common files for the RiscV64 and other archs.
   - CpuDxe/Ia32X64/Amd/        # Ia32 and X64 AMD specific implementation.
                   /            # Common files for Ia32 and X64 archs.
           /ArmAArch64/         # Arm and AArch64 implementation of CpuDxe.
           /                    # Common files for the Arm, AArch64, Ia32 and X64.
```

* If the implementation does not have any shared code between phases (e.g.
MdeModulePkg/Universal/PCD). The guideline below is applied to all CPU architectures support, specific CPU architecture and vendors support, or the implementation is shared by certain CPU architectures:

```
<Feature>/<Phase>[/<CpuArch>[/<Vendor>]]

   <Feature>      REQUIRED    *
   <Phase>        REQUIRED    Base, Sec, Pei, Dxe, DxeRuntime, Mm, StandaloneMm, Smm,
                              Uefi.
   <CpuArch>      OPTIONAL    The <CpuArch> is represented with a BNF,
                              <arch> ::='Ia32' | 'X64' | 'Arm' | 'AArch64' | 'RiscV64' |
                                        'LoongArch64' | 'Ebc'
                              <CpuArch> ::= <arch>[<arch>]*

                              Example: Ia32X64Arm or RiscV64LoongArch64
   <Vendor>       OPTIONAL    *
Example:
   Pcd/Dxe/
```

#### 4.2.3 EDKII Library directory

```
<Phase>[<CpuArch>[<Vendor>]]<LibraryClassName>[<Dependency>]
  or
<Phase><LibraryClassName>[<Dependency>]/[<CpuArch>[/<Vendor>]]

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
                                       that the implementation is layered on top of).

Example:
   - BaseXApicLib/
   - SmmIa32X64AmdSmmCpuFeaturesLib/
   - SmmArmAArch64SmmCpuFeaturesLib/
   - BaseMpInitLib/RiscV64/        # RiscV64 specific implementation.
                  /Ia32X64/        # Ia32 and X64 specific implementation.
                  /Ia32X64/Amd     # Ia32 and X64 AMD specific implementation.
                  /ArmAArch64/     # Arm and AAch64 specific implementation.
                  /LoongArch64/    # LoongArch64 specific implementation.
                  /                # Common files for RiscV64, Ia32, X64, Arm, AArch64 and
                                   LoongArch64.
```
