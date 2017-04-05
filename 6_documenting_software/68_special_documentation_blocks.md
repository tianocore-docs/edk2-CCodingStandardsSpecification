<!--- @file
  6.8 Special Documentation Blocks

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

## 6.8 Special Documentation Blocks

A special documentation block is a C or C++ comment block with some additional
markings, so that Doxygen knows it is a piece of documentation that needs to
end up in the generated documentation.

Normally, Doxygen expects special documentation blocks to immediately precede
the syntactic element being documented (Prefix). There is a mechanism to allow
documentation to be placed after the element to be documented (Postfix). Prefix
style comment blocks are described here, while postfix comment blocks are
described in "Putting Documentation after Members" on page 66.

Each code item can have two types of descriptions. Together, a brief
description and a detailed description form the documentation: Both are
semantically optional. More than one brief or detailed description per code
item, however, is not allowed. We require at least one of these descriptions to
be present.

A brief description is short, usually a single line. A detailed description
provides longer and more detailed documentation.

You may place these descriptions in a comment block in several ways:

* Comment blocks will automatically start a brief description which ends at the
  first period followed by a space or new line. For example:

  ```c
  /** Brief description which ends at this dot.
  This sentence begins the detailed description. The detailed description
  continues...
  **/
  ```

* The behavior also exists for multi-line special C++ comments:

  ```c
  /// Brief description which ends at this dot.
  /// This sentence begins the detailed description.
  ```

It is preferred that any special documentation block longer than two lines use
C-style commenting as shown in the first example above. While not required by
Doxygen, we require the blank line between the brief description and the
detailed description.

Within the body of a C-style comment block, Doxygen will ignore any leading
spaces and asterisks, '*'. This means that the first example could be rewritten
as follows without any change in the generated documentation.

```c
/** Brief description which ends at this dot.
 *
 * This sentence begins the detailed description. The detailed
 * description continues...
**/
```

This type of comment decoration is acceptable because the line of '*' along the
left make it easier to determine the extent of the comment.

As you can see, Doxygen is quite flexible. For more information, see the full
Doxygen documentation.
