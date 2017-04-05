<!--- @file
  APPENDIX B Reserved Identifiers

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

# APPENDIX B Reserved Identifiers

|                                 |                    |                  |                  |
| ------------------------------- | ------------------ | ---------------- |----------------- |
| `__bool_true_false_are_defined` |                    | `_Complex_I`     | `_Exit`          |
| `_IOFBF`                        | `_IOLBF`           | `_IONBF`         | `abs`            |
| `abort`                         | `acos`             | `acosf`          | `acosh`          |
| `acoshf`                        | `acoshl`           | `acosl`          | `and`            |
| `and_eq`                        | `asctime`          | `asin`           | `asinf`          |
| `asinh`                         | `asinhf`           | `asinhl`         | `asinl`          |
| `assert`                        | `atan`             | `atan2`          | `atan2f`         |
| `atan2l`                        | `atanf`            | `atanh`          | `atanhf`         |
| `atanhl`                        | `atanl`            | `atexit`         | `atof`           |
| `atoi`                          | `atol`             | `atoll`          | `BUFSIZ`         |
| `bitand`                        | `bitor`            | `bool`           | `bsearch`        |
| `btowc`                         | `cabs`             | `cabsf`          | `cabsl`          |
| `cacos`                         | `cacosf`           | `cacosh`         | `cacosl`         |
| `cacoshf`                       | `cacoshl`          | `calloc`         | `carg`           |
| `cargf`                         | `cargl`            | `casin`          | `casinf`         |
| `casinl`                        | `casinh`           | `casinhf`        | `casinhl`        |
| `catan`                         | `catanf`           | `catanl`         | `catanh`         |
| `catanhf`                       | `catanhl`          | `cbrt`           | `cbrtf`          |
| `cbrtl`                         | `ccos`             | `ccosf`          | `ccosh`          |
| `ccoshf`                        | `ccoshl`           | `ccosl`          | `ceil`           |
| `ceilf`                         | `ceill`            | `cexp`           | `cexpf`          |
| `cexpl`                         | `CHAR_BIT`         | `CHAR_MIN`       | `CHAR_MAX`       |
| `cimag`                         | `cimagf`           | `cimagl`         | `clearerr`       |
| `clock`                         | `clock_t`          | `CLOCKS_PER_SEC` | `clog`           |
| `clogf`                         | `clogl`            | `compl`          | `complex`        |
| `conj`                          | `conjf`            | `conjl`          | `copysign`       |
| `copysignf`                     | `copysignl`        | `cos`            | `cosf`           |
| `cosl`                          | `cosh`             | `coshf`          | `coshl`          |
| `cpow`                          | `cpowf`            | `cpowl`          | `cproj`          |
| `cprojf`                        | `cprojl`           | `creal`          | `crealf`         |
| `creall`                        | `csin`             | `csinf`          | `csinh`          |
| `csinhf`                        | `csinhl`           | `csinl`          | `csqrt`          |
| `csqrtf`                        | `csqrtl`           | `ctan`           | `ctanf`          |
| `ctanl`                         | `ctanh`            | `ctanhf`         | `ctanhl`         |
| `ctime`                         | `CX_LIMITED_RANGE` | `DBL_DIG`        | `DBL_EPSILON`    |
| `DBL_MAX`                       | `DBL_MANT_DIG`     | `DBL_MAX_10_EXP` | `DBL_MAX_EXP`    |
| `DBL_MIN`                       | `DBL_MIN_10_EXP`   | `DBL_MIN_EXP`    | `DECIMAL_DIG`    |
| `difftime`                      | `div`              | `div_t`          | `double_t`       |
| `EDOM`                          | `EILSEQ`           | `EOF`            | `ERANGE`         |
| `erf`                           | `erff`             | `erfl`           | `erfc`           |
| `erfcf`                         | `erfcl`            | `errno`          | `exit`           |
| `EXIT_FAILURE`                  | `EXIT_SUCCESS`     | `exp`            | `expf`           |
| `expl`                          | `exp2`             | `exp2f`          | `exp2l`          |
| `expm1`                         | `expm1f`           | `expm1l`         | `fabs`           |
| `fabsf`                         | `fabsl`            | `false`          | `fclose`         |
| `fdim`                          | `fdimf`            | `fdiml`          | `FE_ALL_EXCEPT`  |
| `FE_DFL_ENV`                    | `FE_DIVBYZERO`     | `FE_DOWNWARD`    | `FE_INEXACT`     |
| `FE_INVALID`                    | `FE_OVERFLOW`      | `FE_TONEAREST`   | `FE_TOWARDZERO`  |
| `FE_UNDERFLOW`                  | `FE_UPWARD`        | `feclearexcept`  | `fegetenv`       |
| `fegetexceptflag`               | `feholdexcept`     | `fegetround`     | `feof`           |
| `FENV_ACCESS`                   | `fenv_t`           | `feraiseexcept`  | `ferror`         |
| `fesetenv`                      | `fesetexceptflag`  | `fesetround`     | `fetestexcept`   |
| `feupdateenv`                   | `fexcept_t`        | `fflush`         | `fgetc`          |
| `fgetpos`                       | `fgetwc`           | `fgetws`         | `fgets`          |
| `FILE`                          | `FILENAME_MAX`     | `float_t`        | `floor`          |
| `floorf`                        | `floorl`           | `FLT_DIG`        | `FLT_EPSILON`    |
| `FLT_EVAL_METHOD`               | `FLT_MANT_DIG`     | `FLT_MAX`        | `FLT_MAX_10_EXP` |
| `FLT_MAX_EXP`                   | `FLT_MIN`          | `FLT_MIN_10_EXP` | `FLT_MIN_EXP`    |
| `FLT_RADIX`                     | `FLT_ROUNDS`       | `fma`            | `fmaf`           |
| `fmax`                          | `fmaxf`            | `fmaxl`          | `fmin`           |
| `fminf`                         | `fminl`            | `fmod`           | `fmodf`          |
| `fmodl`                         | `fopen`            | `FOPEN_MAX`      | `FP_CONTRACT`    |
| `FP_FAST_FMA`                   | `FP_FAST_FMAF`     | `FP_FAST_FMAL`   | `FP_ILOGB0`      |
| `FP_ILOGBNAN`                   | `FP_INFINITE`      | `FP_NAN`         | `FP_NORMAL`      |
| `FP_SUBNORMAL`                  | `FP_ZERO`          | `fpclassify`     | `fputc`          |
| `fputs`                         | `fpos_t`           | `fprintf`        | `fputwc`         |
| `fputws`                        | `fread`            | `free`           | `freopen`        |
| `frexp`                         | `frexpf`           | `frexpl`         | `fscanf`         |
| `fseek`                         | `fsetpos`          | `ftell`          | `fwide`          |
| `fwprintf`                      | `fwrite`           | `fwscanf`        | `getc`           |
| `getchar`                       | `getenv`           | `gets`           | `getwc`          |
| `getwchar`                      | `gmtime`           | `HUGE_VAL`       | `HUGE_VALF`      |
| `HUGE_VALL`                     | `hypot`            | `hypotf`         | `hypotl`         |
| `I`                             | `ilogb`            | `ilogbf`         | `ilogbl`         |
| `imaginary`                     | `imaxdiv_t`        | `imaxabs`        | `imaxdiv`        |
| `INFINITY`                      | `INT_FASTN_MIN`    | `INT_FASTN_MAX`  | `int_fastN_t`    |
| `INT_LEASTN_MIN`                | `INT_LEASTN_MAX`   | `int_leastN_t`   | `INT_MAX`        |
| `INT_MIN`                       | `INTMAX_C`         | `INTMAX_MAX`     | `INTMAX_MIN`     |
| `intmax_t`                      | `INTN_C`           | `INTN_MIN`       | `INTN_MAX`       |
| `intN_t`                        | `intptr_t`         | `INTPTR_MIN`     | `INTPTR_MAX`     |
| `isalnum`                       | `isalpha`          | `isblank`        | `iscntrl`        |
| `isdigit`                       | `isfinite`         | `isgraph`        | `isgreater`      |
| `isgreaterequal`                | `isinf`            | `isless`         | `islessequal`    |
| `islessgreater`                 | `islower`          | `isnan`          | `isnormal`       |
| `isprint`                       | `ispunct`          | `isspace`        | `isunordered`    |
| `isupper`                       | `iswalnum`         | `iswalpha`       | `iswblank`       |
| `iswcntrl`                      | `iswctype`         | `iswdigit`       | `iswgraph`       |
| `iswlower`                      | `iswprint`         | `iswpunct`       | `iswspace`       |
| `iswupper`                      | `iswxdigit`        | `isxdigit`       | `jmp_buf`        |
| `L_tmpnam`                      | `labs`             | `LC_ALL`         | `LC_COLLATE`     |
| `LC_CTYPE`                      | `LC_MONETARY`      | `LC_NUMERIC`     | `LC_TIME`        |
| `LDBL_DIG`                      | `LDBL_EPSILON`     | `LDBL_MANT_DIG`  | `LDBL_MAX`       |
| `LDBL_MAX_EXP`                  | `LDBL_MAX_10_EXP`  | `LDBL_MIN`       | `LDBL_MIN_EXP`   |
| `LDBL_MIN_10_EXP`               | `ldexp`            | `ldexpf`         | `ldexpl`         |
| `ldiv`                          | `ldiv_t`           | `lgamma`         | `lgammaf`        |
| `lgammal`                       | `llabs`            | `lldiv`          | `lldiv_t`        |
| `LLONG_MAX`                     | `LLONG_MIN`        | `llrint`         | `llrintf`        |
| `llrintl`                       | `llround`          | `llroundf`       | `llroundl`       |
| `localeconv`                    | `localtime`        | `log`            | `logf`           |
| `logl`                          | `log10`            | `log10f`         | `log10l`         |
| `log1p`                         | `log1pf`           | `log1pl`         | `log2`           |
| `log2f`                         | `log2l`            | `logb`           | `logbf`          |
| `logbl`                         | `LONG_MAX`         | `LONG_MIN`       | `longjmp`        |
| `lrint`                         | `lrintf`           | `lrintl`         | `lround`         |
| `lroundf`                       | `lroundl`          | `mal`            | `malloc`         |
| `MATH_ERREXCEPT`                | `math_errhandling` | `MATH_ERRNO`     | `MB_CUR_MAX`     |
| `MB_LEN_MAX`                    | `mblen`            | `mbrlen`         | `mbrtowc`        |
| `mbsinit`                       | `mbstate_t`        | `mbstowcs`       | `mbsrtowcs`      |
| `mbtowc`                        | `memchr`           | `memcmp`         | `memcpy`         |
| `memmove`                       | `memset`           | `mktime`         | `modf`           |
| `modff`                         | `modfl`            | `NAN`            | `nan`            |
| `nanf`                          | `nanl`             | `NDEBUG`         | `nearbyint`      |
| `nearbyintf`                    | `nearbyintl`       | `nextafter`      | `nextafterf`     |
| `nextafterl`                    | `nexttoward`       | `nexttowardf`    | `nexttowardl`    |
| `not`                           | `not_eq`           | `NULL`           | `or`             |
| `or_eq`                         | `offsetof`         | `perror`         | `pow`            |
| `powf`                          | `powl`             | `PRIdN`          | `PRIiN`          |
| `PRIoN`                         | `PRIuN`            | `PRIXN`          | `PRIxN`          |
| `PRIdLEASTN`                    | `PRIdFASTN`        | `PRIdMAX`        | `PRIdPTR`        |
| `PRIiLEASTN`                    | `PRIiFASTN`        | `PRIiMAX`        | `PRIiPTR`        |
| `printf`                        | `PRIoLEASTN`       | `PRIoFASTN`      | `PRIoMAX`        |
| `PRIoPTR`                       | `PRIuLEASTN`       | `PRIuFASTN`      | `PRIuMAX`        |
| `PRIuPTR`                       | `PRIXLEASTN`       | `PRIxLEASTN`     | `PRIXFASTN`      |
| `PRIxFASTN`                     | `PRIXMAX`          | `PRIxMAX`        | `PRIXPTR`        |
| `PRIxPTR`                       | `PTRDIFF_MAX`      | `PTRDIFF_MIN`    | `ptrdiff_t`      |
| `putc`                          | `putchar`          | `puts`           | `putwc`          |
| `putwchar`                      | `qsort`            | `raise`          | `rand`           |
| `RAND_MAX`                      | `realloc`          | `remainder`      | `remainderf`     |
| `remainderl`                    | `remove`           | `remquo`         | `remquof`        |
| `remquol`                       | `rename`           | `rewind`         | `rint`           |
| `rintf`                         | `rintl`            | `round`          | `roundf`         |
| `roundl`                        | `scalbn`           | `scalbnf`        | `scalbnl`        |
| `scalbln`                       | `scalblnf`         | `scalblnl`       | `scanf`          |
| `SCHAR_MAX`                     | `SCHAR_MIN`        | `SCNdN`          | `SCNdFASTN`      |
| `SCNdLEASTN`                    | `SCNdMAX`          | `SCNdPTR`        | `SCNiN`          |
| `SCNiFASTN`                     | `SCNiLEASTN`       | `SCNiMAX`        | `SCNiPTR`        |
| `SCNoN`                         | `SCNoFASTN`        | `SCNoLEASTN`     | `SCNoMAX`        |
| `SCNoPTR`                       | `SCNuN`            | `SCNuFASTN`      | `SCNuLEASTN`     |
| `SCNuMAX`                       | `SCNuPTR`          | `SCNxN`          | `SCNxFASTN`      |
| `SCNxLEASTN`                    | `SCNxMAX`          | `SCNxPTR`        | `SEEK_CUR`       |
| `SEEK_END`                      | `SEEK_SET`         | `setbuf`         | `setjmp`         |
| `setlocale`                     | `setvbuf`          | `SHRT_MAX`       | `SHRT_MIN`       |
| `SIG_ATOMIC_MAX`                | `SIG_ATOMIC_MIN`   | `sig_atomic_t`   | `SIG_DFL`        |
| `SIG_ERR`                       | `SIG_IGN`          | `SIGABRT`        | `SIGFPE`         |
| `SIGILL`                        | `SIGINT`           | `signal`         | `signbit`        |
| `SIGSEGV`                       | `SIGTERM`          | `sin`            | `sinf`           |
| `sinl`                          | `sinh`             | `sinhf`          | `sinhl`          |
| `SIZE_MAX`                      | `size_t`           | `snprintf`       | `sprintf`        |
| `sqrt`                          | `sqrtf`            | `sqrtl`          | `srand`          |
| `sscanf`                        | `stderr`           | `stdin`          | `stdout`         |
| `strcat`                        | `strchr`           | `strcmp`         | `strcoll`        |
| `strcpy`                        | `strcspn`          | `strerror`       | `strftime`       |
| `strlen`                        | `strncat`          | `strncmp`        | `strncpy`        |
| `strpbrk`                       | `strrchr`          | `strspn`         | `strstr`         |
| `strtod`                        | `strtof`           | `strtoimax`      | `strtok`         |
| `strtol`                        | `strtold`          | `strtoll`        | `strtoul`        |
| `strtoull`                      | `strtoumax`        | `strxfrm`        | `swprintf`       |
| `swscanf`                       | `system`           | `tan`            | `tanf`           |
| `tanl`                          | `tanh`             | `tanhf`          | `tanhl`          |
| `tgamma`                        | `tgammaf`          | `tgammal`        | `time`           |
| `time_t`                        | `TMP_MAX`          | `tmpfile`        | `tmpnam`         |
| `tolower`                       | `toupper`          | `towlower`       | `towupper`       |
| `towctrans`                     | `true`             | `trunc`          | `truncf`         |
| `truncl`                        | `UCHAR_MAX`        | `UINT_FASTN_MAX` | `uint_fastN_t`   |
| `UINT_LEASTN_MAX`               | `uint_leastN_t`    | `UINT_MAX`       | `UINTMAX_C`      |
| `UINTMAX_MAX`                   | `uintmax_t`        | `UINTN_C`        | `UINTN_MAX`      |
| `uintN_t`                       | `UINTPTR_MAX`      | `uintptr_t`      | `ULLONG_MAX`     |
| `ULONG_MAX`                     | `ungetc`           | `ungetwc`        | `USHRT_MAX`      |
| `va_arg`                        | `va_copy`          | `va_end`         | `va_list`        |
| `va_start`                      | `vfprintf`         | `vfscanf`        | `vfwprintf`      |
| `vfwscanf`                      | `vprintf`          | `vscanf`         | `vsnprintf`      |
| `vsprintf`                      | `vsscanf`          | `vswprintf`      | `vswscanf`       |
| `vwprintf`                      | `vwscanf`          | `WCHAR_MAX`      | `WCHAR_MIN`      |
| `wchar_t`                       | `wcscat`           | `wcschr`         | `wcscmp`         |
| `wcscoll`                       | `wcscpy`           | `wcscspn`        | `wcsftime`       |
| `wcslen`                        | `wcsncat`          | `wcsncmp`        | `wcsncpy`        |
| `wcspbrk`                       | `wcsrchr`          | `wcsrtombs`      | `wcsspn`         |
| `wcsstr`                        | `wcstod`           | `wcstof`         | `wcstoimax`      |
| `wcstok`                        | `wcstol`           | `wcstold`        | `wcstoll`        |
| `wcrtomb`                       | `wcstombs`         | `wcstoul`        | `wcstoull`       |
| `wcstoumax`                     | `wcsxfrm`          | `wctob`          | `wctomb`         |
| `wctrans`                       | `wctrans_t`        | `wctype`         | `wctype_t`       |
| `WEOF`                          | `WINT_MAX`         | `WINT_MIN`       | `wint_t`         |
| `wmemchr`                       | `wmemcmp`          | `wmemcpy`        | `wmemmove`       |
| `wmemset`                       | `wprintf`          | `wscanf`         | `xor`            |
| `xor_eq`                        | `_Imaginary_I`     |                  |                  |
