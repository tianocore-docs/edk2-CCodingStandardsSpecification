<!--- @file
  4.5 Global & Module Variables

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

## 4.5 Global & Module Variables

There is often confusion about what constitutes module variables versus global
variables. Technically, both global and module variables are defined at file
scope with external linkage. A module variable is intended to only be accessed
across a small set of related routines that have strict rules for accessing the
data; in effect, constrained to the set of files described within a single .inf
file. A global variable is intended to be accessed throughout the firmware,
usually indirectly through a protocol pointer or similar mechanism.

This is important when the time comes to maintain a module. A module variable
should be fairly safe and easy to change because it is only accessed from a
small number of routines. On the other hand, a global variable is accessed
throughout the firmware and as the firmware evolves more code will tend to
access the data resulting in a large number of uses to track down.

### 4.5.1 Recommendations for Global and Module Variables

#### 4.5.1.1 The use of global and module data is strongly discouraged.

Global variables are appropriate for GUID, protocol, PPI definitions and other
immutable objects. Attempting to create global variables can cause many
problems, including: increased image size and variables actually residing in
ROM.

The use of global and module variables may be appropriate for solving certain
programming issues. A module is defined to be a set of data and routines that
act on that data. Thus, in EFI a protocol could be thought of as a module. A
complicated protocol may be built out of several smaller modules.

#### 4.5.1.2 Use locking to protect access to global and module variables.

This protection is strongly encouraged and especially useful for data that is
accessed at various task priority levels.
