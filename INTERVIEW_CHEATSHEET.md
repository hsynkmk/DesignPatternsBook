# 🚀 Design Patterns Interview Cheat Sheet

**Read this 30 minutes before the interview.** All 23 GoF patterns compressed: **what · when · 5-line code feel.**

> 💡 The interviewer rarely asks "implement Visitor on the whiteboard." They ask: **"Have you used patterns? Which? Why?"** — so what matters is **recognition** and **trade-offs**.

**Want the full lessons?** Each pattern below links to a quick-reference file. For the in-depth,
intuition-first course (with refactoring exercises), start at the
[course home](README.md) → [Foundations](00-Foundations/README.md) ·
[Creational](01-Creational/README.md) · [Structural](02-Structural/README.md) ·
[Behavioral](03-Behavioral/README.md) · [Modern & Enterprise](04-Modern-and-Enterprise/README.md) ·
[Choosing a Pattern](05-Practice-and-Beyond/02.Choosing-a-Pattern.md).

---

## 🧭 Quick Triage: "What kind of problem is this?"

| If the problem is about… | Look for a… | Category |
|--------------------------|-------------|----------|
| Creating objects flexibly | **Creational** pattern | 5 patterns |
| Composing objects / adapting interfaces | **Structural** pattern | 7 patterns |
| Communication / responsibility between objects | **Behavioral** pattern | 11 patterns |

---

## 🟢 Creational (5) — *how objects are made*

| Pattern | One-liner | Use it when | Smell |
|---------|-----------|-------------|-------|
| [**Singleton**](Singleton.md) | One instance, global access | Logger, config, connection pool | Hidden global state, hard to test |
| [**Factory Method**](FactoryMethodPattern.md) | Subclass decides which class to instantiate | "I know I need an Animal, not which" | `if (type)` chains in constructors |
| [**Abstract Factory**](AbstractFactoryPattern.md) | Make **families** of related objects | Cross-platform UI (WinButton + WinCheckbox) | Multi-platform / theme switching |
| [**Builder**](Builder.md) | Step-by-step construction of complex objects | Object with many optional fields | Telescoping constructors |
| [**Prototype**](Prototype.md) | Clone an existing object instead of building anew | Object creation is expensive | Repeated identical setup |

```csharp
// Singleton (Lazy<T> — best practice in C#)
public sealed class Logger {
    private static readonly Lazy<Logger> _i = new(() => new Logger());
    public static Logger Instance => _i.Value;
    private Logger() { }
}

// Builder
new HttpRequestBuilder().WithUrl("...").WithHeader("X","Y").WithRetry(3).Build();

// Factory Method
abstract class Dialog { protected abstract Button CreateButton(); }
class WindowsDialog : Dialog { protected override Button CreateButton() => new WindowsButton(); }
```

---

## 🟡 Structural (7) — *how objects are composed*

| Pattern | One-liner | Use it when | Sibling confusion |
|---------|-----------|-------------|-------------------|
| [**Adapter**](Adapter.md) | Make incompatible interfaces work together | Wrapping a legacy/third-party API | Vs Facade: Adapter changes interface to **expected**; Facade simplifies a complex one |
| [**Bridge**](Bridge.md) | Decouple abstraction from implementation | "Shape × Renderer" — both vary independently | Vs Adapter: Bridge is **designed up-front**; Adapter is retro-fit |
| [**Composite**](Composite.md) | Treat individual objects and groups uniformly | Trees: file system, UI, AST | "Tree-shaped data with same operations on leaf + node" |
| [**Decorator**](Decorator.md) | Add behavior dynamically without subclassing | Stream wrappers (`BufferedStream(GZipStream(...))`) | Vs Inheritance: layered at runtime, composable |
| [**Facade**](Facade.md) | Simple interface over a complex subsystem | Hide a tangled library behind one class | Vs Adapter: Facade simplifies; Adapter translates |
| [**Flyweight**](Flyweight.md) | Share fine-grained objects to save memory | Game tiles, glyphs, particles | Split state: **intrinsic** (shared) vs **extrinsic** (per-instance) |
| [**Proxy**](Proxy.md) | Stand-in that controls access to another object | Lazy load, caching, access control, remoting | Same interface as the real thing — Decorator adds behavior |

```csharp
// Decorator (classic stream chain)
Stream s = new GZipStream(new BufferedStream(File.OpenRead("a.txt")), CompressionMode.Decompress);

// Adapter
class LegacyToModernAdapter : IModern {
    private readonly LegacyApi _legacy;
    public string GetData() => _legacy.fetch_old_data();   // translates
}

// Proxy (virtual, for lazy loading)
class ImageProxy : IImage {
    private RealImage? _real;
    public void Display() { _real ??= new RealImage(_path); _real.Display(); }
}
```

---

## 🔵 Behavioral (11) — *how objects communicate*

| Pattern | One-liner | Use it when |
|---------|-----------|-------------|
| [**Chain of Responsibility**](ChainOfResponsibility.md) | Pass a request through a chain until handled | Middleware pipelines, ASP.NET request pipeline, log filters |
| [**Command**](Command.md) | Encapsulate a request as an object | Undo/redo, queues, macros, transactions |
| [**Iterator**](Iterator.md) | Sequentially access elements without exposing structure | C# `IEnumerable<T>`/`yield return` is this pattern |
| [**Mediator**](Mediator.md) | Centralize complex object communication | UI dialogs where N controls talk to each other |
| [**Memento**](Memento.md) | Capture & restore object state | Undo, save points, snapshots |
| [**Observer**](Observer.md) | Publish-subscribe; notify dependents on change | Events, reactive UIs, model→view updates |
| [**State**](State.md) | Behavior changes when internal state changes | Workflow engines, vending machine, TCP connection states |
| [**Strategy**](Strategy.md) | Swap algorithm at runtime | Sorting comparator, payment methods, compression algorithms |
| [**Template Method**](TemplateMethod.md) | Skeleton in base, steps overridden in subclass | Build pipeline w/ fixed order, customizable steps |
| [**Visitor**](Visitor.md) | Add operations to object structures without modifying them | Compilers/interpreters, document tree operations |

```csharp
// Strategy
interface ISortStrategy { void Sort(int[] arr); }
class QuickSortStrategy  : ISortStrategy { /*...*/ }
class MergeSortStrategy  : ISortStrategy { /*...*/ }
class Sorter { public Sorter(ISortStrategy s) { _s = s; } /*...*/ }

// Observer
publisher.PriceChanged += (sender, args) => Console.WriteLine(args.NewPrice);

// Command + undo stack
interface ICommand { void Execute(); void Undo(); }
class TextEditor { Stack<ICommand> _history = new(); /*...*/ }

// State
class Order {
    private IOrderState _state = new NewState();
    public void Pay()    => _state = _state.Pay(this);
    public void Ship()   => _state = _state.Ship(this);
    public void Cancel() => _state = _state.Cancel(this);
}
```

---

## 🆚 Easy-to-Confuse Pairs (interviewers love these)

### Strategy vs State
- **Strategy**: client picks the algorithm, swaps it explicitly. Strategies don't know each other.
- **State**: object transitions itself between states based on context. States often know the next state.

### Adapter vs Facade vs Decorator vs Proxy
| | Same interface? | Adds behavior? | Purpose |
|---|---|---|---|
| **Adapter** | No (translates) | No | Make interfaces compatible |
| **Facade** | No (new, simpler) | No | Simplify a subsystem |
| **Decorator** | Yes | Yes | Add behavior dynamically |
| **Proxy** | Yes | No (controls access) | Lazy load / access control / remoting |

### Factory Method vs Abstract Factory
- **Factory Method**: one method, returns one product. Subclasses override.
- **Abstract Factory**: object with multiple factory methods, produces a **family** of related products.

### Builder vs Factory
- **Factory**: hides which concrete class is created.
- **Builder**: step-by-step construction of one complex object (think: fluent API).

### Composite vs Decorator
Both use recursive composition. **Composite** = treat group as one (structural). **Decorator** = wrap one to add behavior (also structural, but "chain" not "tree").

### Mediator vs Observer
- **Observer**: one subject → many observers, broadcast.
- **Mediator**: many ↔ many through a central hub. Mediator can be implemented using Observer.

### Template Method vs Strategy
- **Template Method**: inheritance — base class defines flow.
- **Strategy**: composition — flow is in the client; algorithm is injected.

---

## 💬 Likely Interview Questions

1. **"Which patterns have you used in production?"**  
   → Pick 2-3 you've actually used. Common honest answers: **Strategy, Observer, Factory Method, Singleton, Decorator** (streams), **Command** (CQRS).

2. **"Singleton — what's wrong with it?"**  
   → Hidden global state, hard to unit-test, hard to mock, lifecycle confusion in DI containers. In modern .NET, register a service as singleton in DI **instead of** writing the pattern manually.

3. **"How does `IEnumerable<T>` / `yield return` relate to GoF patterns?"**  
   → It's the **Iterator pattern** with language support. The compiler generates a state machine for you.

4. **"Strategy vs State — same UML, what's the difference?"**  
   → Intent. Strategy = swap algorithm from outside. State = behavior changes as object's internal state evolves.

5. **"How do design patterns relate to SOLID?"**  
   → Patterns are concrete recipes; SOLID is the principles behind them. Strategy/Template Method enable OCP. Decorator obeys OCP + ISP. Adapter and DI realize DIP.

6. **"When NOT to use a pattern?"**  
   → When it adds indirection without solving an actual problem. "Pattern fever" — applying patterns prophylactically — is a real anti-pattern.

7. **"Show me a refactor that introduces a pattern."**  
   → Walk through `if (paymentType == "card") { ... } else if (paymentType == "crypto") { ... }` → introduce `IPaymentProcessor` (Strategy) and a registry (or Factory).

---

## 🌐 Modern .NET Equivalents (mention these — shows current knowledge)

| Classical pattern | Modern .NET version |
|------------------|---------------------|
| Singleton | `services.AddSingleton<T>()` in DI container |
| Factory | `IServiceProvider`, `IHttpClientFactory` |
| Strategy | Inject the interface; or `Func<T, R>` |
| Observer | C# `event` keyword, `IObservable<T>` (Rx), `INotifyPropertyChanged` |
| Iterator | `IEnumerable<T>`, `yield return` |
| Chain of Responsibility | ASP.NET Core middleware (`app.Use(...)`) |
| Decorator | Scrutor / DI decorators, stream wrappers |
| Proxy | Castle DynamicProxy, EF Core lazy loading |
| Mediator | **MediatR** library (CQRS) |
| Command | MediatR `IRequest`, undo stacks |

---

## ⚠️ Anti-Patterns to Recognize

- **God Object** — one class doing everything (SRP violation)
- **Singleton Abuse** — used for globals, not for true single-instance constraints
- **Anemic Domain Model** — domain objects with only properties, all logic in services
- **Service Locator** — hides dependencies, makes testing hard
- **Pattern Fever** — patterns applied without an actual problem to solve

---

## 🎯 30-Second Talking Points (memorize)

> "Design patterns are reusable solutions to recurring object-oriented problems, organized into three families: **creational** (how objects are made), **structural** (how they're composed), and **behavioral** (how they communicate). The patterns matter less than the underlying principles — most of them realize SOLID. The skill that earns points isn't memorizing them but **recognizing** which one fits a problem, **explaining trade-offs**, and **knowing when not to use one**."

---

## 📚 Recommended Resources
- *Design Patterns: Elements of Reusable OO Software* — GoF (the original)
- *Head First Design Patterns* — Freeman & Robson (most readable intro)
- [refactoring.guru/design-patterns](https://refactoring.guru/design-patterns) — best free resource, with C# examples
