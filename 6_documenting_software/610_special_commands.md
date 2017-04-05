<!--- @file
  6.10 Special Commands

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

## 6.10 Special Commands

All Doxygen commands start with an "at" sign (@). A commands may have one or
more arguments. The following typographic conventions are used to identify each
arguments range:

* If **<**sharp**>** braces are used, the argument is a single word.

* If **(**round**)** braces are used, the argument extends until the end of the
  line on which the command was found.

* If **{**curly**}** braces are used, the argument extends until the next
  paragraph. Paragraphs are delimited by a blank line or by a section indicator.

* If **[**square**]** brackets are used, the argument is optional.

The following sections describe the special Doxygen commands.

### 6.10.1 @example <file-name>

Indicates that a comment block contains documentation for a source code example.

### 6.10.2 @file [ <name> ]

Indicates that a comment block contains documentation for a source or header
file with name <name>. If the file name is omitted, Doxygen uses the name of the
file that contains the `@file` command. This is the preferred method.

### 6.10.3 @attention { attention text }

Starts an indented paragraph where you can enter a message about an issue that
needs attention.

### 6.10.4 @param[in,out] <parameter-name> { parameter description }

Starts a parameter description for a function parameter named <parameter-name>.

### 6.10.5 @post { description of a postcondition }

Starts an indented paragraph where you can describe a postcondition of an
entity.

### 6.10.6 @pre { description of a precondition }

Starts an indented paragraph where you can describe a precondition of an entity.

### 6.10.7 @retval <return value> { description }

Starts a description of a return value from a function. Include a separate
`@retval` for each unique return value.

### 6.10.8 @return { description of what is returned }

Starts a description for a function's return values when those values aren't
easily described by `@retval` commands (that is, the return values are something
other than a small set of unique values with discrete meanings).

### 6.10.9 @sa { references }

Starts a paragraph where you can specify one or more cross-references to
functions, structures, variables, files, or URLs.

### 6.10.10 @since { text }

This tag can be used to specify when (version or time) an entity is available.

### 6.10.11 @test { paragraph describing a test case }

Starts a paragraph where you can describe a test case. The description will
also add the test case to a separate test list. The two instances of the
description will be cross-referenced. Each test case in the test list will be
preceded by a header that indicates the origin of the test case.

### 6.10.12 @todo { paragraph describing what is to be done }

Starts a paragraph where a TODO item is described. The description will also
add an item to a separate TODO list. The two instances of the description will
be cross-referenced. Each item in the TODO list will be preceded by a header
that indicates the origin of the item.

### 6.10.13 HTML Commands

For greater control over the format of generated documentation, you may add
HTML commands to special documentation blocks. "HTML Character Entities" below
lists the special HTML character entities that Doxygen recognizes.

"HTML Commands" lists the HTML commands that you may use inside the
documentation.

Finally, to put invisible comments inside comment blocks, you may use HTML
style comments:

```
/** <!-- This is a comment within a comment block --> Visible text */
```

###### Table 11 HTML Character Entities

| Entity     | Description                                                                                  |
| ---------- | -------------------------------------------------------------------------------------------- |
| `&copy;`   | Copyright symbol                                                                             |
| `&tm;`     | Trade mark symbol                                                                            |
| `&reg;`    | Registered trade mark symbol                                                                 |
| `&lt`      | Less-than symbol                                                                             |
| `&gt`      | Greater-than symbol                                                                          |
| `&amp;`    | Ampersand                                                                                    |
| `&apos;`   | Single quotation mark (straight)                                                             |
| `&quot;`   | Double quotation mark (straight)                                                             |
| `&lsquo;`  | Left single quotation mark                                                                   |
| `&rsquo;`  | Right single quotation mark                                                                  |
| `&ldquo;`  | Left double quotation mark                                                                   |
| `&rdquo;`  | Right double quotation mark                                                                  |
| `&ndash;`  | En-dash (for numeric ranges, e.g. 2-8)                                                       |
| `&mdash;`  | Em-dash (for parenthetical punctuation-like this)                                            |
| `&?uml;`   | Where ? is one of {A,E,I,O,U,Y,a,e,i,o,u,y}, writes a character with a diaeresis accent (ä). |
| `&?acute;` | Where ? is one of {A,E,I,O,U,Y,a,e,i,o,u,y}, writes a character with an acute accent (á).    |
| `&?grave;` | Where ? is one of {A,E,I,O,U,a,e,i,o,u,y}, writes a character with a grave accent (à).       |
| `&?circ;`  | Where ? is one of {A,E,I,O,U,a,e,i,o,u,y}, writes a character with a circumflex accent (â).  |
| `&?tilde;` | Where ? is one of {A,N,O,a,n,o}, writes a character with a tilde accent (ã).                 |
| `&szlig;`  | Sharp s (ß).                                                                                 |
| `&?cedil;` | Where ? is one of {c,C}, writes a c-cedille (ç).                                             |
| `&?ring;`  | Where ? is one of {a,A}, writes an 'a' with a ring (å).                                      |
| `&nbsp;`   | A non breaking space.                                                                        |

###### Table 12 HTML Commands

| `Command`        | `Description`                                               |
| ---------------- | ----------------------------------------------------------- |
| `<A HREF="...">` | Starts an HTML hyper-link.                                  |
| `<A NAME="...">` | Starts a named anchor.                                      |
| `</A>`           | Ends a link or anchor.                                      |
| `<B>`            | Starts a piece of text displayed in a bold font.            |
| `</B>`           | Ends a `<B>` section.                                       |
| `<BODY>`         | Does not generate any output.                               |
| `</BODY>`        | Does not generate any output.                               |
| `<BR>`           | Forces a line break.                                        |
| `<CENTER>`       | Starts a section of centered text.                          |
| `</CENTER>`      | Ends a section of centered text.                            |
| `<CAPTION>`      | Starts a caption. Use within a table only.                  |
| `</CAPTION>`     | Ends a caption. Use within a table only.                    |
| `<CODE>`         | Starts a piece of text displayed in a typewriter font.      |
| `</CODE>`        | End a `<CODE>` section.                                     |
| `<DD>`           | Starts an item description.                                 |
| `<DFN>`          | Starts a piece of text displayed in a typewriter font.      |
| `</DFN>`         | Ends a `<DFN>` section.                                     |
| `<DIV>`          | Starts a section with a specific style                      |
| `</DIV>`         | Ends a section with a specific style                        |
| `<DL>`           | Starts a description list.                                  |
| `</DL>`          | Ends a description list.                                    |
| `<DT>`           | Starts an item title.                                       |
| `</DT>`          | Ends an item title.                                         |
| `<EM>`           | Starts a piece of text displayed in an italic font.         |
| `</EM>`          | Ends a `<EM>` section.                                      |
| `<FORM>`         | Does not generate any output.                               |
| `</FORM>`        | Does not generate any output.                               |
| `<HR>`           | Writes a horizontal rule.                                   |
| `<H1>`           | Starts an unnumbered section.                               |
| `</H1>`          | Ends an unnumbered section.                                 |
| `<H2>`           | Starts an unnumbered subsection.                            |
| `</H2>`          | Ends an unnumbered subsection.                              |
| `<H3>`           | Starts an unnumbered sub subsection.                        |
| `</H3>`          | Ends an unnumbered sub subsection.                          |
| `<I>`            | Starts a piece of text displayed in an italic font.         |
| `<INPUT>`        | Does not generate any output.                               |
| `</I>`           | Ends a `<I>` section.                                       |
| `<IMG>`          | This command is written with attributes to the HTML output. |
| `<LI>`           | Starts a new list item.                                     |
| `</LI>`          | Ends a list item.                                           |
| `<META>`         | Does not generate any output.                               |
| `<MULTICOL>`     | Ignored by Doxygen.                                         |
| `</MUTLICOL>`    | Ignored by Doxygen.                                         |
| `<OL>`           | Starts a numbered item list.                                |
| `</OL>`          | Ends a numbered item list.                                  |
| `<P>`            | Starts a new paragraph.                                     |
| `</P>`           | Ends a paragraph.                                           |
| `<PRE>`          | Starts a pre-formatted fragment.                            |
| `</PRE>`         | Ends a pre-formatted fragment.                              |
| `<SMALL>`        | Starts a section of text displayed in a smaller font.       |
| `</SMALL>`       | Ends a `<SMALL>` section.                                   |
| `<SPAN>`         | Starts an inline text fragment with a specific style.       |
| `</SPAN>`        | Ends an inline text fragment with a specific style.         |
| `<STRONG>`       | Starts a section of bold text.                              |
| `</STRONG>`      | Ends a section of bold text.                                |
| `<SUB>`          | Starts a piece of text displayed in subscript.              |
| `</SUB>`         | Ends a `<SUB>` section.                                     |
| `<SUP>`          | Starts a piece of text displayed in superscript.            |
| `</SUP>`         | Ends a `</SUP>` section.                                    |
| `<TABLE>`        | Starts a table.                                             |
| `</TABLE>`       | Ends a table.                                               |
| `<TD>`           | Starts a new table data element.                            |
| `</TD>`          | Ends a table data element.                                  |
| `<TR>`           | Starts a new table row.                                     |
| `</TR>`          | Ends a table row.                                           |
| `<TT>`           | Starts a piece of text displayed in a typewriter font.      |
| `</TT>`          | Ends a `<TT>` section.                                      |
| `<KBD>`          | Starts a piece of text displayed in a typewriter font.      |
| `</KBD>`         | Ends a `<KBD>` section.                                     |
| `<UL>`           | Starts an unnumbered item list.                             |
| `</UL>`          | Ends an unnumbered item list.                               |
| `<VAR>`          | Starts a piece of text displayed in an italic font.         |
| `</VAR>`         | Ends a `</VAR>` section.                                    |
