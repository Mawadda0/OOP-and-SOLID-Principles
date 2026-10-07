# OOP Study Notes (C++)

A personal reference for revising Object-Oriented Programming. The notes cover the core ideas of OOP in a fixed structure, with a C++ example for each concept, so any topic can be reviewed quickly without re-reading a whole book or course.

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

| # | File | What it covers |
|---|---|---|
| 1 | [Introduction to OOP](1_Introduction_to_OOP.md) | Programming paradigms, why OOP, classes and objects, attributes and methods, constructors, the four pillars |
| 2 | [Encapsulation](2_Encapsulation.md) | Bundling data and behavior, access modifiers, getters and setters |
| 3 | [Inheritance](3_Inheritance.md) | Parent and child classes, overriding, constructors in inheritance, composition, association, aggregation |
| 4 | [Abstraction](4_Abstraction.md) | Abstract classes, interfaces, and when to use each |
| 5 | [Polymorphism](5_Polymorphism.md) | Compile-time and run-time polymorphism, overloading, overriding, common mistakes |
| 6 | [Extras](6_Extras_Static_and_Object_Lifecycle.md) | Optional: static members, the `this` pointer, object lifecycle, stack vs. heap |

Suggested order: read the files from 1 to 5 in sequence, since inheritance, abstraction, and polymorphism build on each other. File 6 is optional and can be read at any point after file 1.

---

## The Four Pillars at a Glance

| Pillar | Idea | Keywords |
|---|---|---|
| Encapsulation | Bundle data and behavior, and control access to them | Access modifiers, getters, setters |
| Inheritance | Reuse code through an is-a relationship | Parent, child, overriding, composition (has-a) |
| Abstraction | Show what an object does, hide how it does it | Abstract class, interface, contract |
| Polymorphism | One call, many forms of behavior | Overloading (compile-time), overriding (run-time) |

A useful way to remember how they connect: encapsulation protects the data, inheritance reuses it, abstraction simplifies how it is used, and polymorphism lets different objects respond to the same call in their own way.

---

## Running the Code

The examples are written for C++17. To compile one, copy it into a `.cpp` file and run:

```bash
g++ -std=c++17 -Wall main.cpp -o main
./main
```

Some snippets in the notes are fragments that focus on one idea. If a snippet has no `main()`, add the includes and a `main()` around it, and use `using namespace std;` as the examples do.

---

## Coming Next

**SOLID principles**, the five design principles that apply OOP well: Single Responsibility, Open/Closed, Liskov Substitution, Interface Segregation, and Dependency Inversion. They appear in the diagram above as the next topic, and they build directly on the four pillars.

---

## Reference Videos

- [Part 1](https://www.youtube.com/watch?v=CnnSDKfnkxk)
- [Part 2](https://www.youtube.com/watch?v=JiyLv0TMMVM)
