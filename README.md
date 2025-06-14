Rust syntax for `joe` and `ne`
==============================

This is an effort to provide an up-to-date and improved Rust language syntax
definition file for *Joe's Own Editor*.\
The file can also be used for the *nice editor*, as it uses the same syntax
definition system (although an earlier version apparently).

Due to the conflicting licenses, this is a complete rewrite, but one that aims
to consider in particular all the issues that came up in recent years (and
were fixed) in the version bundled with `joe`. So we hope this provides an
experience that is at least as good as the old one, with many new features.

**Branches:**
- `main`: For the use with `joe`, employing some of the newer features of the
    JSF syntax
- `ne`: Legacy color scheme for `ne`, similar to the old one and others like
    `c.jsf` etc.
- `ne-alt`: Alternative color scheme for `ne`, for those who might want to try
    something that is a bit different


## Licensing ##

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


## Status ##

Project is in alpha testing phase.

Feedback would be much appreciated.


## List of improvements ##

Base of comparison is `rust.jsf` that is bundled with `joe` version 4.6 at the
time of starting this project (2025).

- Lifetimes
- Number literals:
    - Improved underscore and decimal point parsing (also when using ranges)
    - Improved float exponents
- Characters and strings:
    - Improved escapes, also marking those that are invalid
    - C-string and raw c-string support
    - Slightly improved raw string termination
- Improved prefix support:
    - Raw identifiers and raw lifetimes
    - Marking reserved prefixes and reserved guards
- Support for literal suffixes: marks suspicious tokens that are valid, but
    only when processed by a macro
- Attributes
- Macros
- Option to assign a separate color to control characters as a group, and to
    `!`, `?`, `#` and `$` individually (when they are not part of other
    recognized language structures)
- Updated list of identifiers (Edition 2024)
- Option to highlight the most common special (i.e. derivable and auto) traits
- Improved comments:
    - Separate color class for doc comments, and one just for their starting
        and ending markers
    - Nesting support


## Known limitations ##

The highlighting is not perfect in certain edge cases, due to compromises or
technical restrictions:

- Does not mark deprecated range operators as bad
- Does not enforce the 6 hex digit limitation in Unicode escapes
- In raw strings, when using 5 or more starting hashmarks, the number of
    closing hashmarks is not enforced (terminates at 5, but highlights all)
- Does not recognize those exceptional keywords, that cannot be used even as
    raw identifiers or raw lifetimes
- The list of special traits is somewhat incomplete, because the line had to
    be drawn somewhere (could have included all 30+ traits from core::ops, the
    special types like `Box` and `Rc`, then if we went this far already, why
    leave out anything that is in the Prelude...)
- Traits are not highlighted inside the actual `derive` attribute
- Comment nesting is 4 levels deep maximum
- Non-ASCII characters are not matched specifically, so they may not be
    highlighted correctly (generally they should be okay in char/string
    literals or comments, and in identifier positions there are restrictions
    related to `extern` anyway)

Please provide convincing reasons why we should improve on these topics.
