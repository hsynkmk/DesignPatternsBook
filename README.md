# Design Patterns — A Complete Course (C#)

> **Read this repo top to bottom and you'll go from OOP basics to senior-level pattern fluency.**
> Every pattern starts with a plain-English analogy, shows the *painful code without it*, then the
> clean C# fix, and ends with **refactoring exercises solved in full**. No pattern knowledge assumed.

This isn't an alphabetical reference — it's an **ordered curriculum**. The folders are numbered
`00 → 05`. Read them in order and each topic only relies on what came before.

🎯 **In a hurry before an interview?** Jump to the [Interview Cheat Sheet](INTERVIEW_CHEATSHEET.md).
🧭 **New to patterns?** Start with [What Are Design Patterns](00-Foundations/01.What-Are-Design-Patterns.md).
🤔 **Stuck choosing one?** See [Choosing a Pattern](05-Practice-and-Beyond/02.Choosing-a-Pattern.md).

---

## 🗺️ The Curriculum

| # | Module | What you'll learn | Why it's here |
|---|--------|-------------------|---------------|
| **00** | [Foundations](00-Foundations/README.md) | OOP recap, **SOLID**, composition over inheritance, reading UML | You can't understand patterns without these |
| **01** | [Creational](01-Creational/README.md) | Factory Method, Abstract Factory, Builder, Prototype, Singleton | *How objects are made* |
| **02** | [Structural](02-Structural/README.md) | Adapter, Facade, Decorator, Proxy, Composite, Bridge, Flyweight | *How objects are composed* |
| **03** | [Behavioral](03-Behavioral/README.md) | Strategy, Observer, Command, State, Iterator, and more | *How objects communicate* |
| **04** | [Modern & Enterprise](04-Modern-and-Enterprise/README.md) | DI, Repository/Unit of Work, CQRS, Null Object, Specification | Patterns seniors use daily that GoF predates |
| **05** | [Practice & Beyond](05-Practice-and-Beyond/README.md) | Anti-patterns, choosing a pattern, study plan | Applying it all wisely |

The **23 classic GoF patterns** (Creational + Structural + Behavioral) are all here — including
**Interpreter**, which completes the set.

---

## 🧭 How to Study This

1. **Don't skip Foundations.** [SOLID](00-Foundations/03.SOLID-Principles.md) and
   composition-over-inheritance are the "why" behind every pattern.
2. **Feel the problem first.** Each file shows the painful *before* code — understand the pain
   before the cure.
3. **Do the 🎯 Practice.** These are **refactoring exercises**: take messy code and restructure it
   with the pattern. Attempt before reading the solution.
4. **Learn the comparisons.** Patterns that share a UML but differ in *intent* (State vs Strategy,
   Proxy vs Decorator) are interview favorites — see [Choosing a Pattern](05-Practice-and-Beyond/02.Choosing-a-Pattern.md).
5. **Use the self-check questions** at the end of each file as your "ready to move on?" gate.

A week-by-week roadmap lives in the [Study Plan](05-Practice-and-Beyond/03.Study-Plan.md).

---

## 📐 How Each Pattern Is Structured

Every file follows the same shape — intuition → the problem (before) → structure (UML) → C# (after)
→ trade-offs → when to use/avoid → related patterns → real-world examples → **refactoring practice
with solutions** → takeaways. See [TEMPLATE.md](TEMPLATE.md) for the full spec.

> 💡 The golden rule of this repo: **a pattern is a solution to a recurring problem.** Learn the
> *problem* and the pattern becomes obvious. Memorizing structure without the problem is useless.

---

## 🤝 Contributing

PRs welcome. New content must follow [TEMPLATE.md](TEMPLATE.md) so the learning curve stays
consistent. Open an issue first for anything large.
