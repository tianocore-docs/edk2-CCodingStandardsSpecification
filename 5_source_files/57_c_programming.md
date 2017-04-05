<!--- @file
  5.7 C Programming

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

## 5.7 C Programming

### 5.7.1 Function Definition Layout

Every function should be constructed to the conventions described in this
section.

#### 5.7.1.1 Precede the function with a Doxygen style comment block.

The function header comment block must describe the intent and purpose of the
function, parameters used, and return values.

#### 5.7.1.2 The line immediately following the function header comment block optionally specifies the storage class of the function.

If the storage class is not specified, the return type will be on the first
line following the comment block.

#### 5.7.1.3 The next line of the function definition must specify the function's return type.

If the function does not return a value, this line must contain `VOID`.

#### 5.7.1.4 The next line contains any optional functional modifiers.

For example, `EFIAPI`, or other valid modifiers.

#### 5.7.1.5 The next line contains the function name, left justified, followed by the beginning of the parameter list, "(."

No parameters are allowed on this line. If no parameters are present, it is
acceptable to place the closing parenthesis on the same line, "`(VOID)`".

#### 5.7.1.6 A function that takes no parameters shall be declared with VOID as the parameter list.

Declaring a function with an empty parameter list, `()`, is prohibited.

#### 5.7.1.7 The next lines contain parameters.

Each line will contain a single argument and will start indented two spaces
(one tab stop). Type and argument columns should be aligned to maximize
readability and should include appropriate spacing to ensure this alignment. No
comments are allowed in this region. Parameters are documented clearly in the
function header comment block.

#### 5.7.1.8 The closing parenthesis is on its own line and is also indented two spaces.

A valid exception exists if the function has no parameters.

#### 5.7.1.9 Function prototypes have the same form as function definitions, with the exception of requiring a semicolon after the closing parenthesis of the parameter list.

#### 5.7.1.10 The opening brace of the function body is alone on the next line.

Both the opening and closing brace of the function body must be aligned in the
left most column. All other lines of the function body are indented in
multiples of two spaces.

```c
/** Brief and Detailed Descriptions.

  @param[in]      Arg1  Description of Arg1.
  @param[in]      Arg2  Description of Arg2, which is optional.
  @param[out]     Arg3  Description of Arg3.
  @param[in,out]  Arg4  Description of Arg4.

  @retval  EFI_SUCCESS   Description of what EFI_SUCCESS means.
  @retval  !EFI_SUCCESS  Failure.

--*/
EFI_STATUS
EFIAPI
FooName (
  IN UINTN      Arg1,
  IN UINTN      Arg2, OPTIONAL
  OUT UINTN     *Arg3,
  IN OUT UINTN  *Arg4
  );
{
  UINTN Local;
  ...
}
```

#### 5.7.1.11 Each argument variable's type specification should be preceded by IN and/or OUT modifiers.

The modifiers are used to indicate whether the argument is an input or output
variable. It is strongly suggested that the `IN` variables are first and `OUT`
variables come next. If data is both passed in and passed out through a
variable, then it should be marked as both `IN` and `OUT`. A buffer that is
passed into a routine that modifies the contents of the buffer is marked as
`IN` and `OUT`. "Parameter Modifiers" below describes the usage of the `IN` and
`OUT` modifiers.

The `IN` and `OUT` modifiers may be omitted if the mandatory `@param[in,out]`
descriptions are provided in the function header comment.

###### Table 9 Parameter Modifiers

| Mnemonic   | Description                                                                                                                                         |
| ---------- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| `IN`       | Passed by value. For C, this modifier is any argument whose name **is not** preceded by an asterisk (\*).                                           |
| `IN`       | Passed by reference, and referenced data **is not** modified by the routine. An asterisk precedes the argument name.                                |
| `OUT`      | Passed by reference, and the referenced data **is** modified by the routine. The passed-in state of the referenced data is not used by the routine. |
| `IN OUT`   | Passed by reference, and the passed-in referenced data is consumed and then modified by the routine.                                                |
| `OPTIONAL` | Indicates that if a pointer argument is `NULL`, it is not present. If the value is not `NULL`, then it is a valid argument and may be used.         |

#### 5.7.1.12 The body of a function is contained within open and close braces that must be in the first column.

#### 5.7.1.13 File-Scope data definitions must be the first code in a module.

The type definition must start indented and be followed by the variable name
with at least one indent between the two. Each variable name must have its own
line; do not use a comma to separate multiple declarations. Do not comment data
declarations; they should contain selfdescribing names. If comments are
required for complex data declarations, place the comments in the include file
that defines the complex data type, or make comments in the routine description
block. This restriction does not apply to the members of structures, unions, or
enums.

#### 5.7.1.14 File-Scope Data definitions appearing anywhere but at the beginning of the module are illegal.

#### 5.7.1.15 Function Headings

##### 5.7.1.15.1 Every new function created as part of EDK II must have a function header comment block immediately preceding the function definition.

The function header comment block takes the form shown in the example below.

```c
/**
  Brief description of the function's purpose.

  Detailed description of the function's purpose and how it
  works. Describe algorithms, side-effects, or other attributes
  of the function that would be of use to a programmer unfamiliar
  with the code.

  @param[in] Arg1  Description of Arg1 This can span multiple
                   lines if needed.
  @param[in] Arg2  Description of Arg2.

  @retval  EFI_SUCCESS  Procedure returned successfully.
  @retval  VALUE        Line for each possible return value.
**/
EFI_STATUS
Foo (
  IN UINTN  Arg1,
  IN UINTN  Arg2
  )
{
  // Function body
}
```

##### 5.7.1.15.2 Function comment headings must be present in both the .c file containing the function implementation and in the .h file containing the function prototype.

The function comment heading in the .c file shall, at a minimum, be a
duplicate of the heading in the include file. In all cases, the function
comment heading in the include file is the authoritative source. Function
comment headings in .c files may contain implementation specific comments which
are not permitted in the `.h` file.

##### 5.7.1.15.3 Any function that is shared must have the function prototype in a shared .h file.

Private functions may be declared in the .c file implementing them if they
are not used in any other file. All such private function declarations must be
present at the beginning of the `.c` file, before any function implementations
and after global data.

##### 5.7.1.15.4 All public types, macros, and declarations for a module shall be in a single include file resident in the hierarchy of the top-level include directory of the package the module is part of.

### 5.7.2 Predicate Expressions

#### 5.7.2.1 Boolean values, variable type `BOOLEAN`, do not require explicit comparisons to `TRUE` or `FALSE`.

Non-Boolean comparisons must use a compare operator (`==`, `!=`, `>`, `< >=`,
`<=`).

#### 5.7.2.2 A comparison of any pointer to zero must be done via the `NULL` type.

"Predicate Expression Examples" below shows examples using the following:

```c
BOOLEAN Done;
UINTN Index;
VOID *Ptr;
```

###### Table 10 Predicate Expression Examples

| Incorrect              |       Correct        |
| ---------------------- | -------------------- |
| `if (Index) {`         | `if (Index != 0) {`  |
| `if (!Index) {`        | `if (Index == 0) {`  |
| `if (Done == TRUE) {`  | `if (Done) {`        |
| `if (Done == FALSE) {` | `if (!Done) {`       |
| `if (Ptr) {`           | `if (Ptr != NULL) {` |
| `if (Ptr ==0) {`       | `if (Ptr == NULL) {` |

#### 5.7.2.3 Comparison of unsigned integer types to be >=0 is permitted.

There has been some controversy on this since unsigned integers are always >=0,
and some compilers will emit a warning when this type of construct is seen.
This is perfectly valid code and, with some compilers, is needed for limit
checking against enumerated types. These compilers will assign the type to the
enum based upon the range of values the enum is assigned at compile time.

```
if ((foo >= 0) &&
    (foo < MaxVal))
{ ...
```

If one wants to be perfectly safe in their comparison, the potentially unsigned
term can be cast to a signed integer type of sufficient size; if the range of
possible values is known. `if ((INTN)foo >= 0) { ...`

#### 5.7.2.4 The ordering of terms in predicate expressions may impact performance significantly.

This is because only enough of the expression has to be evaluated to determine
the outcome. For example, the first term in an OR expression that evaluates to
`TRUE` is sufficient to determine that the entire OR expression will be `TRUE`.

The following code sample consists of a predicate expression within a for loop.
The predicate expression is a compound AND expression with four terms. Each
term is itself a simple predicate expression.

This is a real example from a previous version of the EDK II code and was used
in the implementation of the PERF_END functionality. It finds the first open
(EndTimeStamp is zero) performance trace record matching the Handle, Token, and
Module parameters of a PERF_END invocation.

```c
for (Index = 0; Index < NumberOfEntries; Index++) {
  if (( LogEntryArray[Index].Handle == (EFI_PHYSICAL_ADDRESS)(UINTN) Handle)
       && AsciiStrnCmp (LogEntryArray[Index].Token, Token, PEI_PERFORMANCE_STRING_LENGTH) == 0
       && AsciiStrnCmp (LogEntryArray[Index].Module, Module, PEI_PERFORMANCE_STRING_LENGTH) == 0
       && LogEntryArray[Index].EndTimeStamp == 0
     )
  {
    break; // Exit the enclosing for loop.
  }
}
```

While there is nothing really wrong with this code, a little knowledge of the
data it will be working on will allow us to significantly speed things up.
Again taking from a real-world example:

* NumberOfEntries = 25,172

* Target entry is at Index 25,159

* There are 532 completed measurement records with the same Handle, Token, and
  Module values prior to the target.

* There are 6 measurement records with the same Handle and different Token and
  Module values prior to the target.

* There are 25,157 completed entries prior to the target.

From this information, we can see that the terms, in order of importance, are:

1. EndTimeStamp 1 match (2 max over life of a session)

2. Handle 538 matches

3. Module 532 matches

4. Token 532 matches

We also can determine that this ordering is valid for any measurement.
Re-ordering the predicate expression using this information produces:

```c
for (Index = 0; Index < NumberOfEntries; Index++) {
  if ( LogEntryArray[Index].EndTimeStamp == 0
       && LogEntryArray[Index].Handle == (EFI_PHYSICAL_ADDRESS)(UINTN) Handle
       && AsciiStrnCmp (LogEntryArray[Index].Module, Module, PEI_PERFORMANCE_STRING_LENGTH) == 0
       && AsciiStrnCmp (LogEntryArray[Index].Token, Token, PEI_PERFORMANCE_STRING_LENGTH) == 0
     )
  {
    break; // Exit the enclosing for loop.
  }
}
```

The new ordering results in 538 fewer 64-bit integer comparisons and 1,069
fewer string comparisons for this single PERF_END invocation. Considering that
there will be 25,170 PERF_END invocations one can see how the savings add up to
a sizable amount: around 2.7 seconds if the string comparisons only took 100ns
each.

### 5.7.3 Flow Control Statements

#### 5.7.3.1 The body of looping statements must be compound statements.

The `if`, `for`, `do`, and `while` statements shall use a compound statement as
their bodies, even if it is necessary to use a null compound.

#### 5.7.3.2 Null compound statements shall occupy three source lines.

The opening brace shall be on the same line as the controlling keyword,
followed by a line consisting of a properly indented semicolon, then closed
with a closing brace, aligned in the same column as the opening keyword, as the
first non-white-space character on the third line.

#### 5.7.3.3 Any loop that contains no code in the body must use a null compound statement as the body.

For example, the following statement has a null compound for its body.

```c
for (Index = 0; Index < MAX_INDEX; Foo[Index] = Index++) {
  ;
}
```

Avoid this type of construct because it is harder to read than other control
structures.

#### 5.7.3.4 if Statements

##### 5.7.3.4.1 The if statement shall be followed by a space and then the open parenthesis.

* The open parenthesis is followed by a conditional (predicate) expression and
  a close parenthesis.

* There is a space after the close parenthesis followed by an open brace.

* The code body follows and is indented by two spaces.

* The close bracket is on its own line and indented to the same level as the if.

The following is the allowed if construct:

```c
if (TRUE) {
  IamTheCode ();
}
```

##### 5.7.3.4.2 When an else is used, it may start on the same line as the close brace of the if, or be on the following line and aligned with the closing brace.

* A single space must separate `else` from the close and open braces.

* An open brace always follows the `else`.

The following are the allowed `if` and `else` constructs:

```c
if (EXPR_1) {
  IamTheCode ();
} else if (EXPR_2) {
  IamTheCode ();
}
else { // Alternative format
  IamTheCode ();
}
```

#### 5.7.3.5 while and do - while Statements

`while` statements execute their body zero or more times depending upon the
result of a predicate expression. The expression is evaluated at the beginning
of the loop and the body is executed if the expression evaluates to `TRUE`. Code
must be constructed so that nothing outside of the while loop is dependent upon
the body of the loop having been executed.

```c
while (TRUE) {
  IamTheCode ();
}
```

For those cases where the body of the loop must be executed at least once,
there is the do-while statement. In this statement, the predicate is evaluated
at the end of the loop, with the statement's body being re-executed as long as
the predicate evaluates to `TRUE`.

```c
do {
  IamTheCode ();
} while (TRUE);
```

#### 5.7.3.6 for Statements

A `for` loop occupies a minimum of three lines. It is comprised of the `for`
keyword followed by three expressions within parentheses, followed by a
compound statement. The three expressions within parentheses are separated by
semicolons, ';', and consist of the initialization, conditional, and increment
expressions. Any one or combination of these expressions may be omitted if
needed.

```c
for (Index = 0; Index < MAX_INDEX; Index++) {
  IamTheCode (Index);
}
```

#### 5.7.3.7 switch Statements

The following is a switch statement:

```c
switch (Variable) {
case 1:
  IamTheCode ();
  break;

case 2:
  IamTheCode ();
  break;

default:
  IamTheCode ();
  break;
};
```

The case statements are indented either zero tab stops or one tab stop and the
bodies of each case one tab stop from the case.

The closing brace of the switch statement should be in the same column as the
'`s`' in the `switch` keyword.

Always include the `default` case. It should always end with a `break`
statement, even if the `break` is the last thing before the closing brace.

The indenting of the case statements should be consistent with all other
files in the module containing the new .c file. Use the legacy, zero indent,
style if any other file within the module uses that style, otherwise you may
indent a single tab stop.

A descriptive comment is required in cases where the intention is for a
preceding `case` to fall through to the next `case`. That is to say, a
descriptive comment is required where there is no `break` preceding the second
or beyond `case` in a `switch` block.

#### 5.7.3.8 Goto Statements should not be used (in general)

In almost all cases, it is possible to write the code so that a `goto` is not
needed. If a `goto` is used, be ready to defend it during review.

It is common to use `goto` for error handling and thus, exiting a routine in an
error case is the only legal use of a `goto`. A `goto` allows the error exit
code to be contained in one place in the routine. This one place reduces
software life cycle maintenance issues, as there can be one copy of error
cleanup code per routine.

The `goto` follows the normal rules for C code. The label must be indented one
level less than the code it is marking.

```c
Status = IAmTheCode ();
if (EFI_ERROR (Status)) {
  goto ErrorExit;
}

IDoTheWork ();

ErrorExit:
  return Status;
```

The above example could have been rewritten as below, eliminating the need for
a `goto`.

```c
Status = IAmTheCode ();
if (! EFI_ERROR (Status)) {
  IDoTheWork ();
}
return Status;
```

### 5.7.4 Structure Definitions

#### 5.7.4.1 Structure Reference

```c
/** Sample reference to a structure.
 *
 * Sample code showing a reference to a structure as a
 * function parameter. This function should be called as:
 * FooName (&Structure);
 *
 * @param[in] Arg1 A pointer to the sample structure.
**/
VOID
EFIAPI
FooName (
  IN EFI_STRUCTURE_NAME  *Arg1
  );
```

In any situation, definition of structure instances shall be in the following
form:

```
EFI_STRUCTURE_NAME  StructureName;
```

Never pass structures as function parameters by value. Use the "address of"
operator, '`&`', and pass structures by reference.

```
FooName (&StructureName);
```
