<!--- @file
  6.5 Types of Comments

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

## 6.5 Types of Comments

Comments can be either global or internal.

### 6.5.1 Global Comments

Global, or strategic, comments occur outside of function definitions and
provide structural or algorithmic information about the file or program. Global
comments are almost always special Doxygen comment blocks. See Section 6.6
"Introducing Doxygen".

#### 6.5.1.1 Comments are allowed on structure member declarations:

```c
typedef struct {
  EFI_SAMPLE_STRUCTURE *StructurePointer; ///< Sample comment #1
  UINT64               SimpleVariable;    ///< Sample comment #2
} EFI_STRUCTURE_NAME;
```

### 6.5.2 Internal Comments

Internal, or tactical, comments occur within the body of a function definition
and are used to convey special information of use to someone actively reading
the code. These comments are never special Doxygen comments.

#### 6.5.2.1 For internal code comments, use C++ style (//) comment lines.

#### 6.5.2.2 Include a blank line above a block of comment lines containing text.

These blank lines make comments visually distinct without relying on the editor.

#### 6.5.2.3 A blank line may optionally follow a block of comments.

This should generally indicate that the comment is for a large block of code.
No blank line implies that the comment is for the next few lines of code.

#### 6.5.2.4 Comments are allowed on the parameters of a function call.

These comments provide supplemental information about the parameters for that
specific function call. The information in parameter comments should not repeat
the information in the descriptive text for the `@param` entries in the special
documentation block describing the function. Function call parameter comments
are never Doxygen comments.

```c
Status = TestString (
           String,     // Comment for first parameter
           Index + 3,  // Comment for second parameter
           &Value      // Comment for third parameter
           );
```

#### 6.5.2.5 Indent the comments with the code.

This indentation conveys the scope of the comment, as well as maintaining
readability of the code.

```c
/// Do nothing, carefully.
void
NoFun (VOID)
{
  // Only process data if mTest is TRUE.
  // This comment block applies to the entire if/else statement.
  if (mTest) {
    // This is an example comment to explain why this behavior
    // is appropriate if mTest is true.
    // This comment block only applies when mTest is true.

    ThisIsTheCode();
  } else {
    // Explain what we do if (mTest) is false.
    // This comment block only applies when mTest is false.

    ThisIsMoreCode();
  }
}
```
