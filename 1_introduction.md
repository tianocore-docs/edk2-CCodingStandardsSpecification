<!--- @file
  1 Introduction

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

# 1 Introduction

## 1.1 Abstract

This specification establishes a set of rules to:

* Establish uniformity of style.

* Set minimum information content requirements.

* Allow all programmers to easily understand the code.

* Facilitate support tasks by establishing uniform conventions.

* Ease documentation efforts by embedding the design documentation in the code.

* Reduce customer and new employee learning curves by providing accurate code
  documentation and uniform style.

These rules apply to all code developed for inclusion in the EDK II code base,
and are intended as an enabling philosophy. All changes or additions from this
point on shall conform to this specification. Pre-existing code does not need
to be updated for the sole purpose of conforming to this specification. As
conforming updates are made, the developer may update other content within the
modified file to bring it within compliance with this specification. Code
originally developed for other environments that has been ported to, or
modified for, the EDK II environment, is not obligated to conform. However, any
new code added to the ported code must conform.

This specification addresses the chronic problem of providing accurate
documentation of the code base by embedding the documentation within the code.
While this does not guarantee that the documentation will be kept up to date,
it significantly increases the chances. A document generation system, Doxygen,
then produce formatted documentation by extracting information from specially
formatted comment blocks and the syntactic elements of the code.

This specification presents protocol standards that will ensure that the
contractual relationship between APIs and their callers is clear and well
maintained.

This specification describes standard practices designed to eliminate or
mitigate pitfalls inherent in the C language.

In recognition that a coding standard of this size can be a bit daunting, a
concise reference to the standard's key elements is available in "Quick
Reference".

## 1.2 Rationale

Software engineering is much more than writing code that will work one time.
Software engineering entails writing code that:

1. Meets project requirements.

2. Is testable.

3. Can be maintained by the author or by others that have varying degrees of
   experience and familiarity with the code.

4. Minimizes the learning curve for programmers new to the product. (Our
   customers)

We use the C programming language because of its simplicity, flexibility, and
wide support. On the downside in that each developer's C code could
(conceivably) be constructed in totally different and inconsistent ways. This
lack of uniformity makes understanding and maintaining the code very difficult.

Uniformity is the key theme of these rules. You may disagree with some of our
decisions. Nevertheless, we ask that you commit to conforming to standards of
this specification. Also, there are pitfalls inherent in the C language that
this style guide may help you to avoid. The goal of this document is making
you, and those who follow you, more productive.

Some of the strict rules for protocol and driver construction may seem overly
onerous. Don't panic - there is a method to our madness - we intend to
construct wizards to aid in the construction of protocol include files and
device driver templates. The resulting consistency will help prevent name
collision and require much less rote memory (or code surfing) to remember the
names of protocol declarations or GUID definitions.

Good software engineers think about maintaining a consistent and uniform coding
style. Having a set of rules to follow allows them to spend time solving actual
problems and less time thinking about style. Junior software engineers may not
see the benefits, but now is a good time for them to start thinking about what
it will take to maintain their code. Junior software engineers will also
benefit by being able to understand other people's code much more easily
because the code will be written in a consistent manner. Consistency and
uniformity enable productivity.

In conclusion, it's uniformity, uniformity, uniformity. With that said, this
document is not intended to be dogma. However, violating a rule is contingent
on valid reasons for the violation, and the approval of the various
stakeholders involved. It is not something to venture into lightly and is not
recommended.

## 1.3 Scope

This specification describes stylistic conventions and requirements as they
apply to writing C code for inclusion within the EDK II code base. Its bulk is
intended to provide rationale and disambiguating detail for each rule and
requirement. The rules are also presented in summary form for quick reference.
Rationale and detail for each of the rules is then presented in subsequent
sections.

The majority of code produced for EDK II must support multiple compilers and be
able to be retargeted to multiple processor and system architectures. This
requires coding practices to conform to the "lowest common denominator" of the
supported tools, processor, and system architectures.

The C dialect we use is ISO/IEC 9899:199409, or C95, with some elements from
C99 If you are not familiar with this dialect, refer to Harbison and Steele's
_C: A Reference Manual_. This is the language dialect held in common with all
of the compilers supported by EDK II.

**********
**Note:** There are some significant differences between ANSI C (C89) and the
dialect recognized by compilers supported by EDK II (C95). These differences
primarily revolve around use of the external storage class and the elimination
of implicit types and storage classes.
**********

The use of compiler-specific language extensions is very strongly discouraged.

Topics covered in this coding standard include:

* File structure and formats
* C language rules and guidelines
* Naming Conventions
* Documentation
* Commenting rules
* Doxygen

These guidelines represent an attempt make you aware of your actions, because
those actions affect the future readers and maintainers of the code you produce.

Pre-existing code ported to the EDK II environment does not have to conform to
this specification. New code which is added to, or which accompanies, the
ported code must conform.

This specification considers the core firmware, applications, and individual
UEFI drivers as distinct and separate units. This is because UEFI drivers, like
applications, are not linked to the main body of code and do not expose their
internal namespaces to other components of the firmware system.

## 1.4 References

* MISRA-C: _2004 Guidelines for the use of the C language in critical systems_,
  Tyler Doering http://www.misra-c.com, _Guidelines for the Use of the C
  Language in Critical Systems_, ISBN 978-1-906400-10-1 (paperback), ISBN
  978-1-906400-11-8 (PDF), March 2013.

* _Universal Principles of Design_ by William Lidwell, Kritina Holden, and Jill
  Butler. ISBN 159253-007-9.

* _C: A Reference Manual_ by Samuel P. Harbison III and Guy L. Steele Jr. ISBN
  0-13-089592x.

* _Enough Rope to Shoot Yourself in the Foot_ by Allen I. Holub. ISBN
  0-07-029689-8.

* _Code Complete_ by Steven C. McConnell. ISBN 1-55615-484-4.

* _The C Programming Language_ by Brian W. Kernighan and Dennis M. Ritchie.
  ISBN 0-13110362-8.

* ISO/IEC 9899: 1990, Programming Languages - C. This specifies ANSI C.

* ISO/IEC 9899: 199409, Programming Languages - C. This specifies C95.

* ISO/IEC 9899: 1999; Cor-3, Programming Languages - C. This specifies C99.

* Writing Solid Code by Steve Maguire. ISBN 1-55615-551-4.

* EFI Application Toolkit Project Engineering Conventions. 10/4/1999.

* ISO/IEC 6592: 2000, Information Technology - Guidelines for the Documentation
  of Computer-based Application Systems.

* ISO/IEC 18019: 2004, Software and System Engineering - Guidelines for the
  Design and Preparation of User Documentation for Application Software.

* _Indian Hill C Style and Coding Standard_ by L.W. Cannon, R.A. Elliott, L.W.
  Kirchhoff, J.H. Miller, J.M. Milner, R.W. Mitze, E.P. Schan, N.O. Whittington,
  Bell Labs; Henry Spencer, Zoology Computer Systems, University of Toronto;
  David Keppel, EECS, UC Berkeley CS&E, University of Washington; Mark Brader,
  SoftQuad Incorporated, Toronto. 6/25/1990.

* _Doxygen manual_, https://www.doxygen.org/manual/, Version 1.4.6-NO

* _Doxygen Primer_ by Daryl McDaniel, IBM 2002; Updated for Intel Corporation
  1/2006

* _UEFI Specification_, https://www.uefi.org

* _Beyond Bios:Developing with the Unified Extensible Firmware Interface_,
  Second Edition, Zimmer, Michael Rothman, Suresh Marisetty Copyright @2010
  Intel Corporation ISBN 13 978-1-934053-29-4

## 1.5 Glossary

**ANSI**

American National Standards Institute

**C**

The generic name for the C Programming Language. Originally finalized as an
ANSI standard in 1989 ('C89') and updated in 1999 ('C99'). Subsequently adopted
by the ISO (ISO/IEC 9899:1990), which has replaced the ANSI standard, even in
the US.

**CVS**

Concurrent Versioning System

**EFI**

Extensible Firmware Interface

**ISO**

International Standards Organization

**SVN**

The Subversion revision management system.

**Tab Stop**

EDK II uses space characters instead of Horizontal Tab characters. If the
left-most column is column 1, then every odd numbered column is a Tab Stop.
Code elements are aligned at Tab Stops.
