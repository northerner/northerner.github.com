---
title: Managing Haskell versions
---

The need for a tool to manage language versions can be a little confusing for
new developers, but as soon as you're working professionally with legacy
projects the need to have multiple versions of the same language installed
becomes clear.

Projects built years apart will have different dependencies, each
expecting different language runtimes. Manually managing different interpreters
and build tools in your [path](https://en.wikipedia.org/wiki/PATH_(variable))
is painful, and just not practical.

As a Ruby user, my first exposure to language version managers was with RVM and
rbenv. Eventually I moved to chruby, a lightweight manager written in shell
script, and it worked great for me for several years. However, when you being 
to work with multiple languages, each with their own version managers, the
appeal of a single, modular tool becomes clear.

## asdf

asdf is that modular tool. I moved to it a couple of years ago for managing Ruby
and Javascript versions, and would recommend it in most cases.

Until recently I had been using it for Haskell too, which was fine for my simple
beginner projects. However, I have started to work on bigger projects with
several dependencies, and to do this I've been using Stack build tool.

## Haskell, Stack and Cabal

Most tutorials will tell Haskellers to start with just GHC, the Haskell
compiler. I think part of this comes out of the slightly messy story it has
around tooling. As well as Stack which pulls packages from a repository called
Stackage, there's an older packaging tool called Cabal. Cabal is used by Stack,
but it has its own package respoitory, and its own share of
[issues](https://en.wikipedia.org/wiki/Cabal_(software)#Criticism) around
dependency management.

I'm still trying to understand where the differences and best practice around
packaging and managing dependencies.

This all recently led me to this error:

```haskell
‘fail’ is not a (visible) method of class ‘Monad’
```

That line was highlighted in red, along with a few others, when I attempted to
build a new Stack project with a lot of dependencies. It left me with a failing
build and Googling for answers offered few clues.

The error message suggested to pin the version of the "primitive" library, a
dependency somewhere in the tree.
