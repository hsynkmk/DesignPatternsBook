# Design Patterns in C#

The 23 GoF (Gang of Four) design patterns implemented in C#, with Mermaid class diagrams, when-to-use notes, and side-by-side anti-pattern comparisons.

> 🎯 **Crunched for time before an interview?** Start with the [Interview Cheat Sheet](INTERVIEW_CHEATSHEET.md) — every pattern boiled down to one line.

---

## 📚 Patterns Catalog

### 🟢 Creational — *how objects are made*
| # | Pattern | One-liner |
|---|---------|-----------|
| 1 | [Singleton](Singleton.md) | One instance, global access (configs, loggers) |
| 2 | [Factory Method](FactoryMethodPattern.md) | Subclass decides which class to instantiate |
| 3 | [Abstract Factory](AbstractFactoryPattern.md) | Create **families** of related objects |
| 4 | [Builder](Builder.md) | Step-by-step construction of complex objects |
| 5 | [Prototype](Prototype.md) | Clone existing objects instead of building anew |

### 🟡 Structural — *how objects are composed*
| # | Pattern | One-liner |
|---|---------|-----------|
| 6 | [Adapter](Adapter.md) | Bridge incompatible interfaces |
| 7 | [Bridge](Bridge.md) | Decouple abstraction from implementation |
| 8 | [Composite](Composite.md) | Treat individual objects and groups uniformly |
| 9 | [Decorator](Decorator.md) | Add behavior dynamically without subclassing |
| 10 | [Facade](Facade.md) | Simple interface over a complex subsystem |
| 11 | [Flyweight](Flyweight.md) | Share fine-grained objects to save memory |
| 12 | [Proxy](Proxy.md) | Stand-in that controls access (lazy, caching, remoting) |

### 🔵 Behavioral — *how objects communicate*
| # | Pattern | One-liner |
|---|---------|-----------|
| 13 | [Chain of Responsibility](ChainOfResponsibility.md) | Pass requests along a chain of handlers |
| 14 | [Command](Command.md) | Encapsulate requests as objects (undo, queues) |
| 15 | [Iterator](Iterator.md) | Sequential traversal of a collection |
| 16 | [Mediator](Mediator.md) | Centralize complex object communication |
| 17 | [Memento](Memento.md) | Capture & restore object state (undo) |
| 18 | [Observer](Observer.md) | Publish-subscribe between objects |
| 19 | [State](State.md) | Behavior changes when internal state changes |
| 20 | [Strategy](Strategy.md) | Swap interchangeable algorithms at runtime |
| 21 | [Template Method](TemplateMethod.md) | Skeleton in base class, customizable steps |
| 22 | [Visitor](Visitor.md) | Add operations to a structure without changing it |

---

## 📐 Each pattern file includes
- **Problem** — the situation that calls for it
- **Solution** — the pattern's core idea
- **Use Cases** — real-world fits
- **C# Implementation** — clean, idiomatic
- **Mermaid class diagram** — visual structure
- **Key benefits & considerations** — trade-offs
- **Variations / anti-pattern warnings** — when *not* to use it

---

## 🗺️ Suggested Study Order (interview prep)

1. **Strategy** — the gateway pattern; you've probably used it without naming it
2. **Singleton + Factory Method** — classics; know their pitfalls
3. **Observer** — events / pub-sub appears everywhere
4. **Decorator vs Proxy vs Adapter vs Facade** — the structural quartet (very common interview question)
5. **Command** — undo, CQRS, queues
6. **State vs Strategy** — interviewer favorite; same UML, different intent
7. **Builder** — fluent APIs
8. **Composite** — tree-shaped data with uniform ops
9. **Template Method vs Strategy** — inheritance vs composition trade-off
10. The rest — recognize them when you see them

---

## 🛠 Setup
```bash
git clone https://github.com/hsynkmk/Design-Patterns.git
cd Design-Patterns
```

**Prerequisites:** Basic C# / OOP, Visual Studio or VS Code.

## 🤝 Contributing
PRs welcome! Fork → branch → commit → push → open PR.
