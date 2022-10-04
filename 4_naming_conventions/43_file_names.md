<!--- @file
  4.3 File Names

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
