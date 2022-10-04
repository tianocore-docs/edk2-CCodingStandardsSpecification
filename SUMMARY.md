<!--- @file
  Summary

  Copyright (c) 2006-2022, Intel Corporation. All rights reserved.<BR>
  Copyright (C) 2022 Advanced Micro Devices, Inc. All rights reserved.<BR>

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

# Summary

* [EDK II C Coding Standards Specification](README.md#edk-ii-c-coding-standards-specification)
* [1 Introduction](1_introduction.md#1-introduction)
  * [1.1 Abstract](1_introduction.md#11-abstract)
  * [1.2 Rationale](1_introduction.md#12-rationale)
  * [1.3 Scope](1_introduction.md#13-scope)
  * [1.4 References](1_introduction.md#14-references)
  * [1.5 Glossary](1_introduction.md#15-glossary)
* [2 Guiding Principles](2_guiding_principles.md#2-guiding-principles)
  * [2.1 Software Design](2_guiding_principles.md#21-software-design)
  * [2.2 Principles for Software Maintenance](2_guiding_principles.md#22-principles-for-software-maintenance)
  * [2.3 Additional Recommendations](2_guiding_principles.md#23-additional-recommendations)
* [3 Quick Reference](3_quick_reference.md#3-quick-reference)
  * [3.1 Naming](3_quick_reference.md#31-naming)
  * [3.2 Formatting](3_quick_reference.md#32-formatting)
  * [3.3 Files: General Rules](3_quick_reference.md#33-files-general-rules)
  * [3.4 Documentation](3_quick_reference.md#34-documentation)
* [4 Naming Conventions](4_naming_conventions/README.md#4-naming-conventions)
  * [4.1 General Naming Rules](4_naming_conventions/README.md#41-general-naming-rules)
  * [4.2 Directory Names](4_naming_conventions/42_file_names.md#42-directory-names)  
  * [4.3 File Names](4_naming_conventions/43_file_names.md#43-file-names)
  * [4.4 Identifiers](4_naming_conventions/44_identifiers.md#44-identifiers)
  * [4.5 Global & Module Variables](4_naming_conventions/45_global_&_module_variables.md#45-global--module-variables)
  * [4.6 Name Space Rules](4_naming_conventions/46_name_space_rules.md#46-name-space-rules)
* [5 Source Files](5_source_files/README.md#5-source-files)
  * [5.1 General Rules](5_source_files/README.md#51-general-rules)
  * [5.2 Spacing](5_source_files/52_spacing.md#52-spacing)
  * [5.3 Include Files](5_source_files/53_include_files.md#53-include-files)
  * [5.4 Code File Structure](5_source_files/54_code_file_structure.md#54-code-file-structure)
  * [5.5 Preprocessor Directives](5_source_files/55_preprocessor_directives.md#55-preprocessor-directives)
  * [5.6 Declarations and Types](5_source_files/56_declarations_and_types.md#56-declarations-and-types)
  * [5.7 C Programming](5_source_files/57_c_programming.md#57-c-programming)
  * [5.8 Error Handling and ASSERT](5_source_files/58_error_handling_and_assert.md#58-error-handling-and-assert)
* [6 Documenting Software](6_documenting_software/README.md#6-documenting-software)
  * [6.1 Documentation Concepts](6_documenting_software/README.md#61-documentation-concepts)
  * [6.2 Comments](6_documenting_software/62_comments.md#62-comments)
  * [6.3 What NOT to Comment](6_documenting_software/63_what_not_to_comment.md#63-what-not-to-comment)
  * [6.4 What You Must Comment](6_documenting_software/64_what_you_must_comment.md#64-what-you-must-comment)
  * [6.5 Types of Comments](6_documenting_software/65_types_of_comments.md#65-types-of-comments)
  * [6.6 Introducing Doxygen](6_documenting_software/66_introducing_doxygen.md#66-introducing-doxygen)
  * [6.7 How Doxygen Works](6_documenting_software/67_how_doxygen_works.md#67-how-doxygen-works)
  * [6.8 Special Documentation Blocks](6_documenting_software/68_special_documentation_blocks.md#68-special-documentation-blocks)
  * [6.9 Putting Documentation after Members](6_documenting_software/69_putting_documentation_after_members.md#69-putting-documentation-after-members)
  * [6.10 Special Commands](6_documenting_software/610_special_commands.md#610-special-commands)
* [APPENDIX A Common Examples](appendix_a_common_examples.md#appendix-a-common-examples)
* [APPENDIX B Reserved Identifiers](appendix_b_reserved_identifiers.md#appendix-b-reserved-identifiers)
* [APPENDIX C Optimization and Performance](appendix_c_optimization_and_performance.md#appendix-c-optimization-and-performance)
---
* Tables
  * [Table 1 Common Opposites](4_naming_conventions/README.md#table-1-common-opposites)
  * [Table 2 EFI Supported Abbreviations](4_naming_conventions/README.md#table-2-efi-supported-abbreviations)
  * [Table 3 EFI Supported Acronyms](4_naming_conventions/README.md#table-3-efi-supported-acronyms)
  * [Table 4 Reserved Keywords](4_naming_conventions/43_identifiers.md#table-4-reserved-keywords)
  * [Table 5 Permissible Escape Sequences (ISO/IEC 9899:1990 6.1.3.4)](5_source_files/README.md#table-5-permissible-escape-sequences-isoiec-98991990-6134)
  * [Table 6 EFI Data Types (slightly modified from UEFI 2.3.1)](5_source_files/56_declarations_and_types.md#table-6-efi-data-types-slightly-modified-from-uefi-231)
  * [Table 7 Modifiers for Common EFI Data Types (reference the UEFI Specification and Beyond Bios)](5_source_files/56_declarations_and_types.md#table-7-modifiers-for-common-efi-data-types-reference-the-uefi-specification-and-beyond-bios)
  * [Table 8 EFI Constants](5_source_files/56_declarations_and_types.md#table-8-efi-constants)
  * [Table 9 Parameter Modifiers](5_source_files/57_c_programming.md#table-9-parameter-modifiers)
  * [Table 10 Predicate Expression Examples](5_source_files/57_c_programming.md#table-10-predicate-expression-examples)
  * [Table 11 HTML Character Entities](6_documenting_software/610_special_commands.md#table-11-html-character-entities)
  * [Table 12 HTML Commands](6_documenting_software/610_special_commands.md#table-12-html-commands)

