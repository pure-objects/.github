# Pure Objects

An organization dedicated to one idea: object programming — not
object-*oriented* programming. An orientation is a direction you are
free to drift from, and mainstream languages let you. We build the
tools — starting with the PureO language — where objects are not the
recommended style but the only grammar.

## The problem

Sixty years after Simula, most "object-oriented" code is procedural
code wearing class syntax: anemic data bags shuttled between static
service layers. Every discipline we invented to contain the damage —
code reviews, linters, style guides — is optional, and optional
disciplines erode under deadline pressure. The result is familiar:
NullPointerExceptions in production, god classes nobody dares touch,
tests that mock half the universe. The word "oriented" was the
loophole all along: it promised a direction, never a destination.

## The idea

Object thinking, as articulated by Elegant Objects, is a small set of
refusals — each one aimed at a specific, well-known wound.

**Objects are immutable.** An object that changes state is an object
whose identity lies: what you tested a moment ago is not what you hold
now. Immutability makes reasoning local and concurrency trivial —
nothing shared can be corrupted, because nothing shared can change.

**There is no null.** A `null` is absence pretending to be a value;
it compiles everywhere and explodes somewhere else. In object
thinking, absence is an object too — one that answers questions
instead of throwing them.

**There are no statics.** A static method is a procedure: it denies
the object, cannot be decorated, and hardwires its dependencies into
every caller. Utility classes are where object thinking goes to die.

**Composition, never inheritance.** Implementation inheritance
couples every descendant to its ancestor's insides; one change up the
chain ripples down forever. Decoration reuses behavior without owning
it — you wrap an object, you don't become it.

**Constructors only bind.** A constructor that computes, validates,
or touches the network is doing work before the object exists.
Construction is naming collaborators; everything else is behavior,
and behavior belongs in methods.

**Fail fast.** Defensive code hides bugs far from where they were
born, then hands the debugger a corpse with no witnesses. Failing
immediately, loudly, at the first broken expectation is a courtesy to
whoever maintains the code next — usually you.

## Why a language

You can follow these principles in Java today — until the first
hurried Friday commit. Conventions decay; grammars do not. That is
why we are building [PureO](https://github.com/pure-objects/pureo):
a JVM language where these principles are not reviewed, they are
parsed. It compiles to plain Java classes any project can consume;
the pitch, the syntax, and the specification live in the repository.

## Lineage

None of this is ours. The principles come from Yegor Bugayenko's
[Elegant Objects](https://www.elegantobjects.org), and the proof that
a language can be built on pure composition comes from the
[EO](https://github.com/objectionary/eo) research project. Our
contribution is industrial: the same radicalism, in a syntax working
teams already read.

## Repositories

- [pureo](https://github.com/pure-objects/pureo) — language
  specification and compiler

## Status

Early days: the [specification](https://github.com/pure-objects/pureo/blob/master/SPECIFICATION.md)
is at v0.1 and the compiler is being built in public. If you have
practiced object thinking and hit the walls of mainstream languages,
open an issue and argue with us — dissent is the point of this phase.
