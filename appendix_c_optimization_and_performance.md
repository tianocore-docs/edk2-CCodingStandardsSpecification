<!--- @file
  APPENDIX C Optimization and Performance

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

# APPENDIX C Optimization and Performance

You might be tempted to use all sorts of clever techniques to optimize the
code. However, this optimization comes at a penalty.

Rob Pike provides these comments on program complexity,
https://www.lysator.liu.se/c/pikestyle.html, _Notes on Programming in C_.

"Most programs are too complicated - that is, more complex than they need to be
to solve their problems efficiently . . . But programs are often complicated at
the microscopic level . . ."

The following are also condensed from Mr. Pike's 1989 _Notes on Programming in
C_

**Rule 1.** Don't guess at optimization
* Prove the bottleneck location, then put in a speed hack.

**Rule 2.** Measure before tuning for speed
* Be judicious. Only tune for speed if absolutely necessary.

**Rule 3.** Use simple algorithms
* Fancy algorithms are slow.

**Rule 4.** Use simple data structures.

Pike believes that these data structures are almost always enough:

* array
* linked list
* hash table
* binary tree

**Rule 5.** Data structures are central to programming; algorithms are not.
