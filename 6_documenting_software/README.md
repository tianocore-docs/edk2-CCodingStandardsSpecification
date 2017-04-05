<!--- @file
  6 Documenting Software

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

# 6 Documenting Software

## 6.1 Documentation Concepts

A program is meant to be read by the programmer, by another programmer at a
future date, and by a machine. In this sense it is a kind of publication.

However, the machine is concerned with whether the program compiles, while
people are necessarily concerned about coding conventions or style.

Sensible and consistently applied typographic (stylistic) conventions are
important to the creation of a clear presentation. Conventions are created to
facilitate clarity, should not become an end in and of themselves. As Rob Pike
points out, we should avoid typographic silliness and decoration:" . . . keep
comments brief and banner free. Say what you want to say in the program, neatly
and consistently. Then move on."

### 6.1.1 Requirements

The EDK II code documentation shall fulfill the following main functions:

#### 6.1.1.1 Instruction

It shall serve as:

* Working instructions (e.g. error and interrupt handling, data archiving, ...)

* A working basis to avoid duplication of work

* A working basis for software maintenance (e.g. updates, upgrades,
  troubleshooting)

* A basis for brief instruction and training of new staff members; simple
  training courses

#### 6.1.1.2 Verification, Validation, and Objective Evidence

* Establishes traceability between the code and product requirements

* Reference for internal and external auditors (product liability, ISO 9001
  certification)

* Facilitates project management and monitoring

* Increases testability of the software

#### 6.1.1.3 Communications

* Establishes an uniform communication basis for:

* All software developers

* Contractors and customers

* Increases software re-usability

* Increases transparency of the software

### 6.1.2 Interfaces or Protocols

The EDK II architecture forces explicit documentation as it encourages the use
of multiple, independent modules. The mechanism for these modules to
communicate is a protocol. A protocol is an instance of an API (a class in C++
vernacular) that is named by a GUID. The GUID defines the data representation
and member functions of a protocol. Any change to the behavior of a protocol
requires the GUID to change. Given this property, each protocol used in EDK II
must have an interface document.
