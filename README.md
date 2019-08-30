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
|          | [#425](https://bugzilla.tianocore.org/show_bug.cgi?id=425) [CCS] clarify line breaking and indentation requirements for multi-line function calls |            |
|          | [#1656](https://bugzilla.tianocore.org/show_bug.cgi?id=1656) Update all Wiki pages for the BSD+Patent license change with SPDX identifiers        |            |
|          | [#607](https://bugzilla.tianocore.org/show_bug.cgi?id=607) Document code comment requirements for spurious variable assignments                   |            |
