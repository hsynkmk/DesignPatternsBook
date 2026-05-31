# Module 03 — Behavioral Patterns

> *How objects communicate.* These patterns manage algorithms, responsibilities, and the flow of
> messages between objects.

This is the biggest GoF group (11 patterns). **Strategy** and **Observer** are the most-used in
real code; start there.

## Contents (in learning order)

| # | Pattern | Intent |
|---|---------|--------|
| 01 | [Strategy](01.Strategy.md) | Swap interchangeable algorithms at runtime |
| 02 | [Observer](02.Observer.md) | One-to-many notification (pub/sub, events) |
| 03 | [Command](03.Command.md) | Encapsulate a request as an object (undo, queues) |
| 04 | [Template Method](04.Template-Method.md) | Fix the skeleton, let subclasses fill steps |
| 05 | [State](05.State.md) | Behavior changes with internal state |
| 06 | [Iterator](06.Iterator.md) | Traverse a collection without exposing it |
| 07 | [Chain of Responsibility](07.Chain-of-Responsibility.md) | Pass a request along a chain of handlers |
| 08 | [Mediator](08.Mediator.md) | Centralize complex object-to-object communication |
| 09 | [Memento](09.Memento.md) | Capture and restore state (undo) |
| 10 | [Visitor](10.Visitor.md) | Add operations to a structure without changing it |
| 11 | [Interpreter](11.Interpreter.md) | Represent and evaluate a grammar |

## After this module you can

- Use Strategy and Observer fluently (you've probably used them unknowingly).
- Distinguish **Strategy vs State** and **Strategy vs Template Method**.
- Build undo with Command/Memento and decoupled events with Observer/Mediator.

---
◀ Prev: [02 — Structural](../02-Structural/README.md) · ▲ [Course home](../README.md) · ▶ Next: [04 — Modern & Enterprise](../04-Modern-and-Enterprise/README.md)
