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
can use Unicode letters in identifiers, so `问候 := "Hello"` is a valid Go
statement. (Please don't start an argument about this example. I just wanted to
show what you can do. What you should/would do is your problem.)

### Keywords

**TODO:** Add the list of Go keywords with short descriptions. Use a semantic
grouping instead of alphabetic order.

### Operators and Delimiters

**TODO:** Add the list of operators and delimiters in a similar fashion.

### Literals

Literals are constants, they are right-hand values. A literal is the
representation of values that we put inside variables. In an example statement
like `a:=5`, `5` is an integer literal which represents the integer constant
that has the value decimal 5. In addition to the ones we will discuss in this
section, there are also composite literals; but we will talk about them later,
in [Expressions](#) section.

#### Integer Literals

Integer literals represent [integer constant](#)s. Go support octal and
hexadecimal literals with the use of prefixes: `0` for octal and `0x` or `0X`
for hexadecimal. For hexadecimal literals, `a-f` digits are case insensitive so
you can use either uppercase, lowercase or a mixture of them.

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

#### Rune Literals

A rune literal represents a rune constant. A rune constant's value is just a
Unicode code point. Rune literals are defined by single quotes wrapping a
character representation of the Unicode code point in alternative ways:

1. The character itself. Since Go source code is Unicode encoded in UTF-8, you
   can use any characters directly inside your code.

   Examples: ```'a' ' ' 'ş' '我'```. (In the examples below, I will keep using
   these same characters.)

   Some people may not like this if they are not using a font that doesn't have
   the glyphs for the code points you typed directly in the code.

2. Hexadecimal and octal representations. These two cannot represent integer
   values above 255. In hexadecimal representation, the integer value for the
   Unicode code point is written with two hexadecimal digits with a leading
   `\x`.

   Examples: ```'\x61' '\x20'``` As you would expect, we cannot represent the
   latter two characters in this form.

   In octal representation, the value is written with 3 octal digits with a
   leading of a single backslash `\`.

   Examples: ```'\141' '\040'```.

   You can actually represent 512 different values (0..511) with three octal
   digits, `777`, compared to 256 different values (0..255) with two hexadecimal
   digits, `ff`. Hexadecimal representation does not allow you to represent any
   value above 255 although by structure. For octal representation, in spite of
   being able to represent values above 255 with three digits; the limit is
   still there and the maximum value a rune literal can have in octal
   representation is `377` (255 decimal). If you try to have a rune literal such
   as ``\400``, your code will not compile.

4. In the other rune representation, `\u` and `\U` escapes are respectively
   followed by 4 and 8 hexadecimal digits.

   Example: ```'\u0061' '\u0020' '\u015f' '\u6211'```
   Example: ```'\U00000061' '\U00000020' '\U0000015f' '\U00006211'```

   In this representation, there illegal values such as surrogate halves and
   values above `10ffff`.

In addition to the escape sequences we have already seen (`\x \ \u \U`), there
are also a small set of special escapes for some characters. Other than these,
rune literals cannot have any other escape sequence.

```
\a   U+0007 alert or bell
\b   U+0008 backspace
\f   U+000C form feed
\n   U+000A line feed or newline
\r   U+000D carriage return
\t   U+0009 horizontal tab
\v   U+000b vertical tab
\\   U+005c backslash
\'   U+0027 single quote  (valid escape only within rune literals)
\"   U+0022 double quote  (valid escape only within string literals)
```

#### String Literals

Strings are concatenation of characters. Go allows us to represent strings in
two forms:

1. **Interpreted String Literals:** This is what we have in many languages. We
   use double quotes `"` to start and stop a string literal. If we want to use
   double quote character inside the string, we escape it with a backslash so
   `\"` is rendered as a single quote. All the escape sequences that are valid
   for rune literals are valid for interpreted string literals, except for the
   single quote escape. `\'` is illegal between double quotes since you don't
   need to escape it. You just type it: `"Go's beauty."`.

   One thing you should note is that, in a rune literal, we can only have one
   Unicode code point. With hexadecimal and octal representations, we can only
   have a 1-byte value. For multi-byte characters, we use \u or \U notations. In
   string literals, however, we can represent multi-byte characters with the
   sequential use of hexadecimal or octal representations in UTF-8 encoding.

   Example: `"\xe6\x88\x91"` is the same as `"\u6211"` which is the same as
   `"我"`. Here, the three-byte number e68891 is UTF-8 encoded version of
   character "我" (which means I/me by the way).

   In other words, in a string literal, `\x` (hexadecimal) and `\` (octal)
   escapes represent *individual bytes* while `\u` and `\U` escapes represent
   individual characters.

2. **Raw String Literals:** We start and finish raw string literals with back
   quotes (a.k.a. back-tick), `` ` ``. A raw string literal can span multiple
   lines in the source code. Backslash character does not have any special
   meaning in a raw string hence it is called raw, it is not interpreted.

   However, there is still one little modification that will happen to your raw
   strings: Carriage return character, `\r`, will be removed. Thus, if you are
   using an editor which ends lines with `\r\n` or `\n\r`, your compiled code
   will have these replaced with `\n`. This is the result of the same principle
   Go follows, keeping things simple by deciding on one thing.

One last thing you should be aware of is representation of accented characters
in unified or composed form. This is not an issue specific to Go; but since spec
mentions it, I didn't want to skip. Unicode has [combining characters](
https://en.wikipedia.org/wiki/Combining_character) and when such a
character follows a normal character, the end result would be the combination of
the accent and the preceding character. For example, "â" can be represented as

- one Unicode code point, "\u00e2" (LATIN SMALL LETTER A WITH CIRCUMFLEX) or
- two Unicode code points, "\u0061\u0302" (LATIN SMALL LETTER A followed by
  COMBINING CIRCUMFLEX ACCENT)

I don't know the latest versions; but I remember a few years ago Mac OS using
combined form in file names and Linux or Windows not being very fond of it.

In my personal view, I very much dislike having *human language* inside code
outside of comments; but if you have issues with your strings, keep these in
mind:

* Your editor: Beware of the encoding of your source code files. For Go, it
must be UTF-8.

* If you are dealing with the file system and targeting multiple platforms, be
  careful about non-ASCII characters in file names, especially characters with
  accents. (I prefer saying "non-ASCII characters instead of how some would call
  those characters "Unicode characters" because ASCII characters are also
  Unicode characters.)

* TODO: add more suggestions.
