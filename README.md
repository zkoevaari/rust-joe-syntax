Rust syntax for `joe` and `ne`
==============================

This is an effort to provide an up-to-date and improved Rust language syntax
definition file for *Joe's Own Editor*.\
The file can also be used for the *nice editor*, as it happens to use the same
syntax definition system.

Due to the conflicting licenses, this is a complete rewrite, although one that
aims to consider in particular all the issues that came up in recent years
(and were fixed) in the version bundled with `joe`. So we hope this provides
an experience that is at least as good as the old one, with many new features.


## Licensing notes ##

To be compatible with both projects, this work is licensed under GPLv2, or (at
your option) any later version.

```
This program is free software; you can redistribute it and/or
modify it under the terms of the GNU General Public License
as published by the Free Software Foundation; either version 2
of the License, or (at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program; if not, see
<https://www.gnu.org/licenses/>.
```


## New features ##

(TODO: recheck, also: compared to what?)
- Number literals:
    - Improved underscore and decimal point parsing
    - Improved float exponents
- Characters and strings:
    - Rules for marking invalid escapes
    - C-string and raw c-string support
    - Slightly improved raw string termination
- Support for Literal suffixes: marks suspicious tokens that are valid, but
    only when processed by a macro


## Known limitations ##

- Does not mark deprecated range operators as bad
- Does not enforce the 6 hex digit limitation in unicode escapes
- In raw strings, when using 5 or more starting hashmarks, the number of
    closing hashmarks is not enforced (terminates at 5, but highlights all)
- Allows char and string literal suffixes starting with a number


## TODO ##

- common traits
- macros (dollar)
- ! bang
- doc comments
- raw identifiers and raw lifetimes
- check \r
- check for possible `noeat` infinite loops
- UTF8 support
