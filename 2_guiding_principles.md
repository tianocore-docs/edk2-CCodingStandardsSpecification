<!--- @file
  2 Guiding Principles

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

# 2 Guiding Principles

This chapter discusses the principles of high-quality software. It is likely
that your design will not be able to achieve all of these goals; if it does,
your design is very good indeed. Note that some of these design goals
contradict other design goals. Contradiction is part of the challenge of doing
a good design.

Maintainability of software is of such importance that those principles are
expanded separately in "Principles for Software Maintenance".

## 2.1 Software Design

The following is an alphabetical list of software design principles:

**Accessibility**

This entails designing objects and environments to be usable, with no
modification, by the greatest number of people possible, including people
with varying educational and social backgrounds, as well as those with motor or
sensory challenges.

**Alignment**

Elements within a design should be aligned with one or more other elements.
Alignment of related or like elements within a design reduces the perception of
disorder and promotes understanding.

**Chunking.**

Chunking groups units of information into a small number of units (maximum of
four plus or minus one) to help the efficient processing of information by
shortterm memory, as well as to accommodate its limits.

**Confirmation.**

This is a technique used for critical actions, inputs, or commands.
Confirmations are primarily used to prevent unintended actions. Minimize errors
in critical or irreversible operations with confirmations. If you overuse
confirmations, expect that they will be ignored. Avoid overusing confirmations
to ensure that they remain unexpected and uncommon; otherwise, they may be
ignored. Use a two-step operation for hardware confirmations and dialogs for
software confirmations.

**Consistency.**

Express similar parts or concepts in similar ways to make a system to improve
usability and learnability. Apply consistency to design and coding style, as
well as user interfaces. Do not apply consistency to the point of compromising
clarity or usability.

**Maintainability**

Design for the maintenance programmer or sustaining engineer for
maintainability, or ease of maintenance. The design of the system should be
self-explanatory.

**Extensibility**

Extensibility entails enhancing a system without violating the underlying
structure. The most likely changes should cause the system the least trauma.
For example, you know the BIOS is responsible for booting the system, so adding
a new type of boot device should not cause trauma to the system. Be careful
about the assumptions you make.

**Forgiveness**

Design to help users avoid errors and reduce the negative consequences of
any errors made. Recommended methods for achieving design forgiveness
include affordances, reversibility of actions, and safety nets. Effectively
designing for forgiveness results in a design needing minimal confirmations,
warnings, and help.

**High fan-in**

Sharing a high number of routines that call a given routine produces high
fan-in. Sharing entails designing a system to make good use of utility routines
at the lower levels.

**Horror Vacui**

This is a Latin phrase for "fear of emptiness", which is the desire to fill
empty spaces with information or objects. Research shows that as _horror vacui_
increases, perceived value decreases. In programming, lines consisting solely
of comment characters, with no actual comment, are good examples of _horror
vacui._

**Intellectual manageability**

Intellectual manageability is a primary goal in any system. It is essential to
the overall system integrity and affects how easily programmers can initially
build a system as well as maintain it later.

**Interference Effects**

When two or more perceptual (or cognitive) processes are in conflict, the
competing mental processes slow down mental processing or make mental
processing less accurate. Examples of this include violations of convention (a
red <font color="red">**OK**</font> light), information conflicts
(a color name, <font color="orange">**GREEN**</font>, in a different color), and
incorrect use of opposites.

**Leanness**

Design the system so that it has no extra parts, i.e. "lean". If you add extra
code, remember that it needs to be developed, reviewed, tested, maintained,
understood, and taken into account when the code is modified. Also, future
versions of the code may have to be backward compatible with the extra code.

**Low complexity**

Low complexity is part of intellectual manageability.

**Minimal connectedness**

Design so that you keep connections among subprograms to a minimum. This
minimizes work during integration, testing, and maintenance. Use industry
standards whenever possible. Make sure you are not reinventing something that
already exists.

**Minimize code size**

Unlike many software engineering projects, EDK II firmware is targeted to be
stored in a device that represents a tangible cost to the system. Thus, the
minimization of code size is important to reduce the overall cost of a system.

**Portability**

Design the system so that it is easily moved to another environment. With EDK
II, making sure the code will run on IA32, X64 and Intel(R) Itanium(R)
processors (IPF) is an example of portability.

**Reusability**

Design the system so that pieces of it can be reused in other systems. In EDK
II, reusability also means designing code so that it can be used in various
classes of platforms from embedded systems to massively parallel computers.

**Standard techniques**

Greater reliance on unique or exotic pieces makes a system harder to
understand, and more intimidating for someone trying to understand it the first
time. Using standardized, common approaches should give the whole system
a familiar feeling. This standardization is one of the primary goals of this
document.

**Stratified design**

In order to view the system at any single level and get a consistent view of
it, you should attempt to keep the levels of decomposition layered. The OSI
multi-layernetworking model is an example of stratified design.

## 2.2 Principles for Software Maintenance

### 2.2.1 Understand the problem before you fix it.

The best way to ruin a code base is to attempt to fix problems without a clear
understanding of the problem itself. If your fix is out of context, the next
fix in the routine will be four times more complicated. Triangulate the error
with cases that should and should not cause the error. Keep at it until you
understand the error.

### 2.2.2 Understand the program, not just the problem.

Understanding the context in which a problem occurs will increase your
likelihood of solving the problem completely.

### 2.2.3 Fix the symptom AND the underlying problem.

Fix the symptom, but your focus should be on fixing the underlying problem.
Without thoroughly understanding the problem, you will not fix the code. You
will also feel very uncomfortable when a peer reviews your fix before you check
it into the source base.

### 2.2.4 Change the code only for good reason.

Do not change code at random until it seems to work; that isn't effective. If
you do this you are not learning anything and are just goofing around. You
should have confidence that a change will work before making a change. Being
wrong about a change should be rare and cause personal reevaluation.

### 2.2.5 Do not debug by superstition.

Don't blame every problem on the computer, bad data, or the effects of a full
moon. You wrote the program; take responsibility for it.

### 2.2.6 Don't blame everyone else's code.

It is human nature to trust the code that you wrote and understand, and to
distrust all other code. You must resist this tendency and root cause the
problem systematically.

### 2.2.7 Don't use source control to debug problems.

You don't debug by randomly trying previous versions of code. You can use
previous versions as a single test of your triangulated test cases. Bugs are
not always introduced by changes. Bugs can lie dormant in a code base for long
periods of time. By blindly rolling back changes, you could just be hiding a
bug, versus fixing one.

### 2.2.8 Check your fix.

Run the triangulated test cases against your code. Have another set of eyes
look at your change, preferably someone who is experienced in the code.

### 2.2.9 Look for similar errors.

Errors tend to occur in groups, so check to make sure a similar mistake was not
made in other parts of the code.

### 2.2.10 Fix the code AND the comments.

When you have correct code but incorrect comments, you will confuse the next
person in the code. Remember, programming is a team sport.

### 2.2.11 Fix the comments AND the documentation.

The next person to make a large change to code will thank you and might even
not camp out in your cube for a week. This has been simplified in EDK II by
embedding the documentation within the comments.

## 2.3 Additional Recommendations

* If you have trouble debugging without violating these rules, please ask for
  help.

* Learn to debug by debugging with someone who is good at it. There is
  (approximately) a 20-to-1 difference in the time it takes an experienced
  programmer to find the same set of errors as an inexperienced programmer.

* Try to not focus only on the bug, but on the process and techniques the
  experienced programmer uses to find bugs.

* When working with a more experienced debugger, your goal should be to improve
  your debugging skills.

* If you rely too heavily on the debugging skills of others, your own expertise
  suffers.
