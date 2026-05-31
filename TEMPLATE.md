# Pattern Template & Contributor Guide

Every pattern file in this course follows the **same shape**. That consistency is what turns a
pile of notes into a *course*: once you've read two patterns, you know exactly where to find the
intuition, the structure, the code, or the practice in every other one.

Copy the skeleton below when adding a pattern. Keep the section order and the emoji headers (they
double as visual anchors when skimming).

---

## The Sections (in order)

1. **`# Pattern: <one-line intent>`** — the title names it; the subtitle is the GoF intent in plain
   words ("define a family of algorithms and make them interchangeable").
2. **`## 🧠 Intuition`** — a real-world analogy / mental model. **No code.** If a smart beginner
   wouldn't follow it, simplify.
3. **`## 🎯 The Problem`** — a concrete scenario and the *painful code without the pattern* (the
   "before"). The reader should feel the pain the pattern relieves.
4. **`## 📐 Structure`** — a **Mermaid class diagram** plus a list of the **participants** and what
   each one's job is.
5. **`## 💻 C# Implementation`** — clean, idiomatic C# that fixes the Problem (the "after").
   Explain the idea language-agnostically first if it helps.
6. **`## ⚖️ Trade-offs`** — honest pros and cons.
7. **`## ✅ When to Use / 🚫 When to Avoid`** — including how the pattern is **misused** (its
   anti-pattern failure mode).
8. **`## 🔗 Related Patterns`** — the comparisons people confuse (e.g. *State vs Strategy*,
   *Proxy vs Decorator*).
9. **`## 🌍 Real-World & .NET Examples`** — where it actually shows up in the framework / BCL / real apps.
10. **`## 🎯 Practice (with full solutions)`** — 2–3 **refactoring exercises**: a code smell or a
    scenario → refactor it to the pattern. Each with a complete C# solution and *why it's better*.
11. **`## ✅ Key Takeaways`** — a tight bullet summary, then **self-check questions**.
12. **Navigation footer** — `◀ Prev` · `▲ Module index` · `▶ Next` relative links.

> **Foundations files** (SOLID, OOP) use a lighter variant: *principle → ❌ bad code → ✅ good code
> → practice → takeaways*.

---

## Conventions

- **Audience:** a developer who knows basic C#/OOP but is new to patterns. Define jargon on first use.
- **Cross-link liberally.** Use relative links like `[SOLID](00-Foundations/03.SOLID-Principles.md)`
  (add `../` across module folders). Linking a not-yet-written file is fine — it marks intent.
- **Diagrams:** Mermaid `classDiagram` blocks render on GitHub. Keep them legible.
- **C# style:** modern idioms — interfaces, `Lazy<T>`, expression members, records where they fit.
  Prefer composition; show the "before/after" so the pattern's value is visible.
- **Tone:** direct and encouraging. Short sentences. The goal is *understanding*, then *applying*.
- **Always show the "before."** A pattern only makes sense against the problem it solves.

---

## Skeleton (copy me)

```markdown
# <Pattern>: <one-line intent>

## 🧠 Intuition
<analogy / mental model — no code>

## 🎯 The Problem
<scenario + the painful "before" code>

## 📐 Structure
\`\`\`mermaid
classDiagram
    ...
\`\`\`
**Participants:** <role → responsibility>

## 💻 C# Implementation
\`\`\`csharp
<clean "after" code>
\`\`\`

## ⚖️ Trade-offs
**Pros:** ...  **Cons:** ...

## ✅ When to Use / 🚫 When to Avoid
<incl. the misuse / anti-pattern>

## 🔗 Related Patterns
<the confusing comparisons>

## 🌍 Real-World & .NET Examples
<where it shows up>

## 🎯 Practice (with full solutions)
### 1. <Refactor scenario> — `Easy`
**Smelly code / scenario:** ...
**Task:** refactor to <pattern>.
**Solution:**
\`\`\`csharp
...
\`\`\`
**Why it's better:** ...

## ✅ Key Takeaways
- ...

**Self-check:** <2–3 questions>

---
◀ [Prev](.) · ▲ [Module index](./README.md) · ▶ [Next](.)
```
