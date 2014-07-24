# Notation

If you are like me with an irresistable passion for learning new languages, you
will be very familiar with
[Metasyntax](https://en.wikipedia.org/wiki/Metasyntax) notations. The spec uses
[EBNF](https://en.wikipedia.org/wiki/Extended_Backus%E2%80%93Naur_Form) for
specifying syntax. Although a metasyntax is very useful to express the rules
very clearly without giving space for any confusion, it is really not the most
readable piece of text. Since the spec already provides this formal
representation, I believe it wouldn't hurt to have a less-concrete; but much
more readable style.

So I will specify Go language syntax in a more visual and easy-to-read fashion.

Let's give this notation a name: *Visform*. I know, it doesn't sound great;
but it is what I got in 3 seconds. I think even by name, it is easier to read
than BNF, WSN, or ABNF. Please don't get me wrong. I don't suggest this as an
alternative to those formal and probably much more comprehensive forms. This is
just good only when served in addition to those.

## Visform

In this representation of syntax, a more visual approach is preferred.
