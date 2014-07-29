# Lexical Elements

Go source code consists of these lexical elements:
- Comments
- Semicolons
- Tokens
  - Identifiers
  - Keywords
  - Operators and Delimiters
  - Literals
      - Integer
      - Floating Point
      - Imaginary
      - Rune
      - String

## Comments

Go supports both
- *line comments* that start with // and stop at the end of the line, and
- *general comments* that are wrapped between `/*` and `*/`.

Line comments and single-line general comments are replaced with a space
character. General comments that span multiple lines are replaced with a newline
character.

Comments do not nest.

## Semicolons

Semicolons are used as terminators in several places; but unlike most other C
family languages, semicolons are automatically inserted. This is very similar to
JavaScript; except that the accepted style is dropping semicolons without any
semicolon wars.

When a line ends with one of these, a semicolon is inserted automatically:

1. an identifier or literal
2. one of these keywords: `break`, `continue`, `fallthrough`, or `return`
3. one of these operators/delimiters: `++`, `--`, `)`, `]`, or `}`

The other rule about semicolons is that you don't need to have a semicolon
before a `)` or `}` since these two delimiters closes a block/list.

I want to emphasize: The idiomatic Go code does not use semicolons at the end of
lines to terminate statements. Newline character is sufficient alone. You can
see this in the standard library. I have read a pretty good amount of Go code,
but I have not seen use of semicolons at the end of lines anywhere except some
testing/trying code of some new learners of the language. The common practice is
not having them.

In JavaScript semicolon-wars, I have seen so many people claiming that the rules
of semicolon insertion is so complex that you should use semicolons instead of
wasting your time learning the rules. Unfortunately, sometimes we are too lazy
to read a few lines of text and understand it. If you skipped the simple rules
above, please study them. It is really not difficult. It is natural, intuitive.
When you code, you never think about it; you just know how.

## Tokens

### Identifiers

Identifiers in Go starts with a letter and continue with letters and digits. You
can use unicode letters in identifiers, so `问候 := "Hello"` is a valid Go
statement. (Please don't start an argument about this example. I just wanted to
show what you can do. What you should/would do is your problem.)

### Keywords

**TODO:** Add the list of Go keywords with short descriptions. Use a semantic
grouping instead of alphabetic order.

### Operators and Delimiters

**TODO:** Add the list of operators and delimiters in a similar fashion.

### Literals

#### Integer Literals

Integer literals represent [integer constant](#)s. Go support octal and hexadecimal
literals with the use of prefixes: `0` for octal and `0x` or `0X` for
hexadecimal. For hexadecimal literals, `a-f` digits are case insensitive so you
can use either uppercase, lovercase or a mixture of them.

TODO: Add information about the idiomatic use of lower/upper cases for
hexadecimals in standard library.

#### Floating-point Literals

Floating-point literals represent [floating-point constant]s. A floating point
literal always have one and only one full stop character `.` and either or both
an integer part preceding the decimal point and a fractional part following the
decimal point.

Fractional part can also have an exponent part which starts with an `e` or `E`
character followed by the decimal exponent. Decimal exponent can be signed with
`+` for positive or `-` for negative. When it is not signed, it is considered
positive.

#### Imaginary Literals

Go natively support imaginary numbers. An imaginary literal is defined by the
`i` suffix added to a token which would normally be either an integer or
floating-point literal.

