# Module 04 — Modern & Enterprise Patterns

> The patterns GoF (1994) didn't cover but that a senior developer uses **every day** in real
> applications — especially in web/back-end and .NET.

These build directly on the GoF foundations: Dependency Injection is "program to an interface"
taken to its conclusion; CQRS leans on Command and Mediator; Repository is a Facade over data.

## Contents

| # | Pattern | Intent |
|---|---------|--------|
| 01 | [Dependency Injection](01.Dependency-Injection.md) | Inject dependencies instead of newing them; Inversion of Control |
| 02 | [Repository & Unit of Work](02.Repository-and-Unit-of-Work.md) | Abstract data access; group writes into one transaction |
| 03 | [CQRS](03.CQRS.md) | Separate the write model from the read model |
| 04 | [Null Object](04.Null-Object.md) | A do-nothing object instead of `null` checks |
| 05 | [Specification](05.Specification.md) | Encapsulate business rules as composable objects |

## After this module you can

- Explain Inversion of Control and wire up the .NET DI container.
- Design a data layer with Repository + Unit of Work, and know its criticisms.
- Recognize when CQRS, Null Object, or Specification clean up real code.

---
◀ Prev: [03 — Behavioral](../03-Behavioral/README.md) · ▲ [Course home](../README.md) · ▶ Next: [05 — Practice & Beyond](../05-Practice-and-Beyond/README.md)
