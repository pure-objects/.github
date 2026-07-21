# PureO

**A JVM language where the compiler enforces object thinking.**

Most object-oriented codebases are object-oriented by convention only:
`null` leaks, statics accumulate, getters expose state, and inheritance
couples everything to everything. Code reviews catch some of it.
Discipline catches a bit more. The rest ships.

PureO takes a different route: it makes the violations inexpressible.
The [Elegant Objects](https://www.elegantobjects.org) principles are
not guidelines here — they are the grammar.

```pureo
interface Money {
  plus(other: Money): Money
  printed(): Text
}

object UsdMoney(amount: Decimal): Money {
  new(cents: Int) = UsdMoney(Decimal.of(cents, 2))
  plus(other: Money): Money = UsdMoney(amount.plus(other.decimal()))
  printed(): Text = Formatted("$%s", amount)
}
```

## What the compiler rejects

- `null` — absence is explicit, always
- Static methods and utility classes
- Getters, setters, and any mutable state
- Implementation inheritance — composition and decoration only
- `instanceof`, casts, and reflection
- Code in constructors — they bind attributes, nothing else

## What you keep

- The JVM: PureO transpiles to plain final Java classes, consumable
  from any Java project as an ordinary JAR
- Java libraries: reachable through an explicit, greppable interop
  construct that types every Java return value as nullable
- A familiar syntax: if you read Java or Kotlin, you read PureO

## Relation to EO

PureO is the industrial sibling of [EO](https://github.com/objectionary/eo),
the research language by Yegor Bugayenko that explores object thinking
through φ-calculus. EO proves the ideas; PureO packages them in a
syntax your team already knows.

## Repositories

- [pureo](https://github.com/pure-objects/pureo) — language
  specification and compiler

## Status

Early days: the [specification](https://github.com/pure-objects/pureo/blob/master/SPECIFICATION.md)
is at v0.1 and the compiler is being built in public. Star the repo,
read the spec, and open an issue to disagree with a design decision —
that is exactly what this phase is for.
