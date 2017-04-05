<!--- @file
  5.8 Error Handling and ASSERT

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

## 5.8 Error Handling and ASSERT

`ASSERT` macros are development and debugging aids and shall never be used for
error handling.

Assertions are used to catch conditions caused by programming errors that are
resolved prior to product release.

The EDK II PCD, `PcdDebugPropertyMask`, can be used to enable or disable the
generation of code associated with `ASSERT` usage. Thus, all code must be able
to operate, and recover in a reasonable manner with `ASSERT`s disabled.

Parameters and conditions that are beyond the programmers control need to be
checked programmatically. Care must be taken, though, to ensure that the need
for programmatic error handling is minimized.

The `ASSERT_EFI_ERROR`, `ASSERT_PROTOCOL_ALREADY_INSTALLED`, and all other
`ASSERT` macros defined in `DebugLib.h` are covered by this rule.
