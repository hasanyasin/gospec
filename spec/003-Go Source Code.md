# Source Code Representation

Go source code is Unicode text encoded in UTF-8. This decision saves us from
hacky solutions like Python's character set hints based on editor-specific
awkward forms such as \-\*\- coding: utf-8 \-\*\-.

The text is not canonicalized: A single accented code point is distinct from
the same character constructed from combination of an accent and a letter which
are treated as two separate code points. Spec refers Unicode code points as
"character" and I will follow the same convention in this document.

Go is case sensitive, foobar, Foobar, and FooBar are all different.

Spec notes as an implementation restriction that a compiler may disallow the NUL
character (U+0000) in Go source text.

Another implementation restriction mentionend in the spec is that UTF-8 encoded
BOM (byte order marks) (U+FEFF) at the beginning of a source text may be ignored
by the compiler. Also, a byte order mark may be disallowed anywhere else in the
source. Since Go source is always UTF-8 and the standard doesn't require or
recommend BOM use since it doesn't mean anything for a UTF-8 stream, this will
never be an issue unless you use some very badly configured editor.

Such decisions and restrictions are little examples of the design approach of
Go platform. Smart limitations make life easier and Go is full of such smart
design decisions.

## Characters

TODO: VisForm for Characters

TODO: List character categories adapted from Unicode Standard 6.3 Section 4.5.

## Letters and Digits

TODO: Visform for letters and digits.

Underscore _ (U+005F) is a special character in Go, blank identifier when it is
used alone. When it is used inside an identifier, it is considered a letter.