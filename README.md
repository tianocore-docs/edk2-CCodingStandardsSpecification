<!--- @file
  README.md for EDK II C Coding Standards Specification

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

<img src="media/TianocoreTitlePageLogo.jpg" width="300" />

### {{ book.title }}

{% if book.draft %}
** DRAFT FOR REVIEW **
{% else %}
** {{ book.version }} **
{% endif %}

** {{ gitbook.time|date('MM/DD/YYYY hh:mm:ss') }} **

{% if book.udkrelease %}
** {{ book.udkrelease }} **
{% endif %}


### Acknowledgements

Redistribution and use in source (original document form) and 'compiled'
forms (converted to PDF, epub, HTML and other formats) with or without
modification, are permitted provided that the following conditions are met:

1. Redistributions of source code (original document form) must retain the
   above copyright notice, this list of conditions and the following
   disclaimer as the first lines of this file unmodified.

2. Redistributions in compiled form (transformed to other DTDs, converted to
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

Copyright (c) 2006-2017, Intel Corporation. All rights reserved.


### Revision History

| Revision | Revision History                                                                                                                                  | Date       |
| -------- | ------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- |
| 0.0.1    | First swag.                                                                                                                                       | 6/23/00    |
| 0.0.2    | Included feedback from team.                                                                                                                      | 8/3/00     |
| 0.3      | Add comments.                                                                                                                                     | 8/10/00    |
| 0.3001   | Pre-vacation update, need to sync with new numbering process.                                                                                     | 9/11/00    |
| 0.31     | Incorporated Sync 1 learnings.                                                                                                                    | 12/12/00   |
| 0.32     | Completed TAT ARs.                                                                                                                                | 6/8/01     |
| 0.33     | Added goto rules.                                                                                                                                 | 8/16/01    |
| 0.34     | Updated to match driver and Runtime Lib.                                                                                                          | 11/15/01   |
| 0.9      | Updated to Intel(R) Platform Innovation Framework for EFI. Added checklist appendix.                                                              | 1/8/04     |
| 0.91     | Completed editing and formatting pass.                                                                                                            | 3/3/04     |
| 0.92     | Updated the structure declaration rules: Added section 4.8 and modified the checklist in Appendix A.                                              | 4/8/04     |
| 0.93     | Added some minor clarifications in section 3.1, 4.5, 7.1, and 10.                                                                                 | 9/14/04    |
| 0.94     | Revised to accommodate Doxygen style commenting standards                                                                                         | 3/1/06     |
| 0.50     | Change to new numbering scheme. Incorporate Review Comments. Editing and formatting.                                                              | 4/21/06    |
| 0.51     | Changed to EDK II.                                                                                                                                | 7/13/06    |
| 0.52     | Update rules to clarify areas of misinterpretation. Add copyright formatting rules.                                                               | 2/09/2010  |
| 0.60     | Re-organize document and update to current rules.                                                                                                 | 2/15/2010  |
| 0.70     | Release for Review                                                                                                                                | 3/1/2010   |
| 0.95     | Review comments incorporated, Release to Tech Pubs for Finalization                                                                               | 3/10/2010  |
| 1.00     | First full release                                                                                                                                | 3/15/2010  |
| 1.01     | Restructure into book format.                                                                                                                     | 12/08/2011 |
| 1.02     | Incorporate suggestions and trackers                                                                                                              | 3/19/2012  |
|          | Release For Review                                                                                                                                | 4/2/2012   |
|          | Release                                                                                                                                           | 4/16/2012  |
| 1.03     | Update and incorporate requests and bug fixes. Remove "Intel Confidential" classification.                                                        | 9/11/2014  |
| 1.50     | Release for Review                                                                                                                                | 9/26/2014  |
| 1.80     | Incorporate US Review Comments                                                                                                                    | 10/10/2014 |
| 1.85     | Incorporate PRC Review Comments                                                                                                                   | 10/24/2014 |
|          | Release for Extended US & PRC Review                                                                                                              | 10/28/2014 |
| 2.0      | Release                                                                                                                                           | 11/14/2014 |
| 2.1      | DRAFT for REFORMAT                                                                                                                                | 10/30/2015 |
| 2.2      | Convert to Gitbook                                                                                                                                | June 2017  |
|          | [GH #9](https://github.com/tianocore-docs/edk2-CCodingStandardsSpecification/issues/9) BZ #425 [Commit 3f1100b](https://github.com/tianocore-docs/edk2-CCodingStandardsSpecification/commit/3f1100beda60843361a9761b43ba7b18adf0d265) [CCS] clarify line breaking and indentation requirements for multi-line function calls | June 2017  |
| 2.3      | BZ #1656 [Commit d096859](https://github.com/tianocore-docs/edk2-CCodingStandardsSpecification/commit/d096859f15b9cde19c230ac391ae21ee409af48c) Update all Wiki pages for the BSD+Patent license change with SPDX identifiers | April 2019 |
|          | [GH #10](https://github.com/tianocore-docs/edk2-CCodingStandardsSpecification/issues/10) BZ #607 [Commit f5ad35e](https://github.com/tianocore-docs/edk2-CCodingStandardsSpecification/commit/f5ad35ec2c6d46e59d2ab999de3147349b102fe5) Document code comment requirements for spurious variable assignments | Sept 2019  |
|          | [GH #10](https://github.com/tianocore-docs/edk2-CCodingStandardsSpecification/issues/10) BZ #607 [Commit 1b4a4cc](https://github.com/tianocore-docs/edk2-CCodingStandardsSpecification/commit/1b4a4cc4e562d431928f45f655cad10cbe2321d0) Restrict and clarify applicability of "/*" comments | Sept 2019  |
|          | [GH #10](https://github.com/tianocore-docs/edk2-CCodingStandardsSpecification/issues/10) BZ #607 [Commit 0f75934](https://github.com/tianocore-docs/edk2-CCodingStandardsSpecification/commit/0f759345cc8aca2249b3b9f222bc22ce28e0dd17) Remove "Horror Vacui" rule | Sept 2019  |
|          | [Commit d2b81c4](https://github.com/tianocore-docs/edk2-CCodingStandardsSpecification/commit/d2b81c41872a094ce4fe2270c8c03cdb75cc8e1c) Fix URLs on the Introduction page | Dec 2020   |
|          | [Commit 0d88b47](https://github.com/tianocore-docs/edk2-CCodingStandardsSpecification/commit/0d88b4742209c162c37f5dab282a1c5990e15aa8) Update Name Space Rules examples to follow coding standard | Dec 2020   |
|          | [Commit 3edad55](https://github.com/tianocore-docs/edk2-CCodingStandardsSpecification/commit/3edad55bd06c99abc318e7716cad6ce45ee2636a) Update Chapter 5 examples to follow coding standard | Dec 2020   |
|          | [Commit 835ab88](https://github.com/tianocore-docs/edk2-CCodingStandardsSpecification/commit/835ab88b06eb87261b98b4ff4cf57a80418302b0) Fix extraneous semicolon in Chapter 5 function example | Dec 2020   |
|          | [Commit 9286fa6](https://github.com/tianocore-docs/edk2-CCodingStandardsSpecification/commit/9286fa6c678cb9c120eb661e07c7e6b622f1ae47) Add Gitbook Action to publish HTML, PDF, EPUB, and MOBI | Oct 2020   |
|          | Add 4.2 Directory names section and update File names section for the guidelines of module directory and file naming                              |September 2022|
|          | [Commit bda6c02](https://github.com/tianocore-docs/edk2-CCodingStandardsSpecification/commit/bda6c0228d33538cc7bb5e1016c3755961904430) Insert Directory Names section | Oct 2022   |
|          | [Commit 782dc33](https://github.com/tianocore-docs/edk2-CCodingStandardsSpecification/commit/782dc33657b4a4a66b416df22785a6d35c9c245e) Updates 4.2 and 4.3 sections | Oct 2022   |
|          | [Commit 275e9e6](https://github.com/tianocore-docs/edk2-CCodingStandardsSpecification/commit/275e9e60b53bd721ad6b9ff4d07cdf6005a0399e) Fix missing hyperlink in section 4.2 | Oct 2022   |
| 2.4      | [Commit bbec647](https://github.com/tianocore-docs/edk2-CCodingStandardsSpecification/commit/bbec647065a435e70772323b9d2d77a1ca00ae7f) Fix Markdown to PDF formatting issue | Nov 2022   |
|          | [GH #21](https://github.com/tianocore-docs/edk2-CCodingStandardsSpecification/issues/21) BZ #1766 [Commit 422e975](https://github.com/tianocore-docs/edk2-CCodingStandardsSpecification/commit/422e9752985ff9b895ac2bc58b31b4e01f05bd00) Remove use of `STATIC` macros from EDK II C Coding Standard Specification | Feb 2025   |
|          | [Commit 7a15a16](https://github.com/tianocore-docs/edk2-CCodingStandardsSpecification/commit/7a15a16adcf1a7785514f352d78a5b99ffd3d3d7) Use github.ref_name in publish action | April 2025 |
|          | [Commit cacfbcf](https://github.com/tianocore-docs/edk2-CCodingStandardsSpecification/commit/cacfbcf3ba6c736a06f424fcf9c2c2d47bcf1ec2) Use publish-gitbook-docs action for document publishing | April 2025 |
|          | [PR #25](https://github.com/tianocore-docs/edk2-CCodingStandardsSpecification/pull/25) Replace include guard macros with `#pragma once` in include files | Feb 2026   |
|          | [GH #19](https://github.com/tianocore-docs/edk2-CCodingStandardsSpecification/issues/19) BZ #723 [PR #26](https://github.com/tianocore-docs/edk2-CCodingStandardsSpecification/pull/26) 5.1.8 Typo: "provided" should be "proven" | March 2026 |
|          | [GH #20](https://github.com/tianocore-docs/edk2-CCodingStandardsSpecification/issues/20) BZ #839 [PR #27](https://github.com/tianocore-docs/edk2-CCodingStandardsSpecification/pull/27) Minor typographical errors in chapters 1-5 | March 2026 |
|          | [GH #24](https://github.com/tianocore-docs/edk2-CCodingStandardsSpecification/issues/24) BZ #4160 [PR #28](https://github.com/tianocore-docs/edk2-CCodingStandardsSpecification/pull/28) Unclear statement for the blank line for comment | March 2026 |
|          | [GH #23](https://github.com/tianocore-docs/edk2-CCodingStandardsSpecification/issues/23) BZ #2664 [PR #29](https://github.com/tianocore-docs/edk2-CCodingStandardsSpecification/pull/29) Fix code examples to match rules and EDK II uncrustify style | March 2026 |
|          | [GH #30](https://github.com/tianocore-docs/edk2-CCodingStandardsSpecification/issues/30) [PR #31](https://github.com/tianocore-docs/edk2-CCodingStandardsSpecification/pull/31) Update Revision History with GitHub Issues/PR links | March 2026 |
