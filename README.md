# OOP & SOLID Study Notes

A personal reference for revising Object-Oriented Programming and SOLID principles. The notes cover the core ideas of OOP and SOLID principles in a concise, fixed structure, accompanied by C++ examples to enable quick revision without going through full books or courses.

The ideas themselves are language independent. C++ is used for the code because it shows what happens under the hood, and the same concepts carry over to Java, C#, Kotlin, and Python with different syntax.

<p align="center">
  <img src="/Media/oop-overview.svg" alt="OOP and SOLID overview"/>
</p>

---

## How to Use This Repo

Each note follows the same layout, so you always know where to look:

1. **Concept**: what the idea means, in a line or two.
2. **Explanation**: why it exists and how it works, with a real-world analogy where one helps.
3. **Code (C++)**: a short example that shows the concept in action.
4. **Diagram**: a sketch of the idea.
5. **Summary**: the key points for last-minute revision.

For a quick review, read only the Concept and Summary sections of each file. For a deeper pass, go through the code and run it.

---

## Contents

### Part 1: OOP Principles

| # | File | What it covers |
|---|---|---|
| 1 | [Introduction to OOP](/OOP-Principles/1_Introduction_to_OOP.md) | Programming paradigms, why OOP, classes and objects, attributes and methods, constructors, the four pillars |
| 2 | [Encapsulation](/OOP-Principles/2_Encapsulation.md) | Bundling data and behavior, access modifiers, getters and setters |
| 3 | [Inheritance](/OOP-Principles/3_Inheritance.md) | Parent and child classes, overriding, constructors in inheritance, composition, association, aggregation |
| 4 | [Abstraction](/OOP-Principles/4_Abstraction.md) | Abstract classes, interfaces, and when to use each |
| 5 | [Polymorphism](/OOP-Principles/5_Polymorphism.md) | Compile-time and run-time polymorphism, overloading, overriding, common mistakes |
| 6 | [Extras](/OOP-Principles/6_Extras_Static_and_Object_Lifecycle.md) | Optional: static members, the `this` pointer, object lifecycle, stack vs. heap |

---

### Part 2: SOLID Principles

| # | File | What it covers |
|---|---|---|
| 7 | [Introduction to SOLID](/SOLID-Principles/1_Introduction_to_SOLID.md) | What SOLID stands for, why code rots, design smell, overview of the 5 principles |
| 8 | [Single Responsibility Principle](/SOLID-Principles/6_Single_Responsibility.md) | Single reason to change, high cohesion, decoupling responsibility |
| 9 | [Open-Closed Principle](/SOLID-Principles/2_Open_Closed.md) | Open for extension, closed for modification, abstraction-driven design |
| 10 | [Liskov Substitution Principle](/SOLID-Principles/3_Liskov_Substitution.md) | Subtype substitutability, contract design, behavioral subtyping |
| 11 | [Interface Segregation Principle](/SOLID-Principles/4_Interface_Segregation.md) | Lean interfaces, avoiding bloated abstractions, client-specific contracts |
| 12 | [Dependency Inversion Principle](/SOLID-Principles/5_Dependency_Inversion.md) | High-level and low-level modules, dependency injection, inversion of control |

**Suggested Order:** Read OOP files (1 to 5) first to grasp object-oriented fundamentals. Then move to SOLID Principles (7 to 12) starting with the Introduction to understand why design principles matter. File 6 can be reviewed anytime after File 1.

---

## Note

Some snippets in the notes are fragments that focus on one idea. If a snippet has no `main()`, add the includes and a `main()` around it, and use `using namespace std;` as the examples do.
