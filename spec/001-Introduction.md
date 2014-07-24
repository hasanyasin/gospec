# Introduction

## About This Document

This is a sugar coated version of the official Go reference manual, which I will
refer to as *spec*.

In this version, I use a different syntax notation, provide additional examples,
and employ an informal language. I sometimes use the exact sentence in the spec;
but most of the time, I express the same ideas in a completely different way. I
refer to external resources time to time when I think it is useful or just fun.

In spite of all the fanciness I try to achieve, I still aim 100% coverage of the
contents of the spec. If I miss a tiny bit of information during this
transformation, please help me fix it by submitting a bug report on [Github
issues](https://github.com/hasanyasin/gospec/issues). To make it easier for you
to follow, I also provide direct access to original text of the spec in every
section of the document.

## About Go Language

Go is a general-purpose language designed with systems programming in mind. It
was originally designed as a minimalist alternative to C++ which is everything;
but minimal. Surprisingly, designers of the language saw that most Go
programmers were coming from languages like Python and Ruby, instead of C++. You
can read further in [this nice
post](http://commandcenter.blogspot.com/2012/06/less-is-exponentially-more.html)
which is actually the text of a given talk at a GO meeting.

### Compiled
Go is not a scripting language. Instead of being interpreted and run by an
interpreter, your code is compiled into native binaries. This has several
advantages beyond the speed such as the ease of deployment. Go compiles very
fast and you can run your code with an on-the-fly compilation like you would run
a script which blurs the difference between compiler and interpreter for the
sake of development ease.

### Strongly Typed
Go is strongly typed. There is no implicit type conversions. Any type error will
slap you in the face during compilation before you push your buggy code to
central repository. This might require a little time to get used to, especially
if you spent most of your development time with scripting languages. However,
you will see that it will make your code more expressive and easier to read. It
will also make it harder to cause some funny bugs.

### Garbage Collected
Go is garbage-collected. Most of the time, this is a good thing. Once you grasp
the different mentality of programming in Go, you will rarely cause any memory
leaks. Even if you do, it will be easy to catch thanks to Go's comprehensive
toolset that is a part of the design of the language as a whole development
environment.

### Concurrency Included
Go has explicit support for concurrent programming. The origin of the ideas
behind Go's concurrency model dates back to a paper published by [C. A. R.
Hoare](https://en.wikipedia.org/wiki/C._A._R._Hoare) in 1978. One of the lead
designers of Go language, [Rob Pike](https://en.wikipedia.org/wiki/Rob_Pike),
had actually implemented Newsqueak, which he calls *a toy language*, with the
same principles. Thanks to concurrency being an important feature of the
language design, instead of a feature provided by a library, building concurrent
systems with advanced features in Go is really simple. You can watch [this video
of a talk](http://www.youtube.com/watch?v=f6kdp27TYZs) by Rob Pike at Google I/O
2012.

### Packages
Go source code is organized into *packages* which can contain a hierarchy of
folders with multiple source files. Go packages make it very easy to share your
code with others and add others' code to your projects. It wouldn't be wrong
saying that Go's packaging is even more convenient than Ruby's gems or Node's
npm. It is definitely more liberal by making it possible sharing a package only
by sharing a public url such as the github link of your repository without a
need for a central repository or package manager system. Packages are defined
by conventions you follow in your code and code organization so there are no
separate files for package definition.

### Minimalist
Go's grammar is compact and regular, allowing for easy analysis by automatic
tools such as development environments. There are no awkward quirks. Semicolons
are added by the compiler automatically similar to JavaScript; but for Go, the
strong convention is **not** to use them at the end of each line. There are no
fights nor flame wars about semicolons or no-semicolons. There is even [a tool](
http://golang.org/cmd/gofmt/) in the standard toolset to *fix* your ugly code by
bringing it to conventional style.

### Go is for You
Go has a very unique approach to many different problems we face every day as
software developers. If you are coming from C, you will feel at home with just
some neat modern updates and without sharp corners. If you have been a Java or
C++ programmer, you will feel like you threw away all the unnecessary furniture
and turned your home into one of those futuristic minimalist houses [you see in
the movies](http://www.imdb.com/media/rm3505174528/tt1104001). If you are coming
from Ruby or Python, you will love Go for giving you a much higher performance
and easier deployment with the same ease of development, if not easier. If you
are coming from Nodejs, you will find Go very interesting for giving you
concurrency in a totally different way. Whoever you are, wherever you are coming
from, Go is a language and *way of programming* that is worth the time you will
invest in learning.