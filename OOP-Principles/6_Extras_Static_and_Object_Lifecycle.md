# 6. Extras: Static Members and Object Lifecycle

This is an extra file. It is not one of the four pillars, but it covers topics that come up often alongside them. It looks at what happens behind the scenes: where data belongs (to the class or to the object), how objects are created and destroyed, and where they live in memory. The examples are in C++, where all of this is visible. In languages like Java, much of it is handled automatically by a garbage collector.

---

## Static Members

### Concept

A `static` member belongs to the class itself, not to any single object. There is only one copy of it, shared by every object of that class.

### Explanation

Normal attributes are per object: each object has its own copy. A static attribute is different. If you want to count how many players have been created, that number cannot live inside one player, because it describes all of them together. It belongs to the class.

A **static method** follows the same idea:

- It can be called without creating an object, using `ClassName::method()`.
- It has no `this` pointer (see below), so it can only touch static members directly. It cannot use normal attributes, because there is no specific object to read them from.

Common uses: counters, constants shared by all objects, and utility functions that do not depend on any object's data.

### Code (C++)

```cpp
#include <iostream>
#include <string>
using namespace std;

class Player {
private:
    string name;
    inline static int count = 0;      // one shared copy (inline static needs C++17)

public:
    Player(string n) : name(n) { ++count; }
    ~Player() { --count; }

    static int getCount() { return count; }   // static method
};

int main() {
    cout << Player::getCount() << "\n";   // 0, no object needed

    Player a("Karim");
    Player b("Sara");
    cout << Player::getCount() << "\n";   // 2

    {
        Player c("Youssef");
        cout << Player::getCount() << "\n";   // 3
    }                                          // c is destroyed here

    cout << Player::getCount() << "\n";   // 2
}
```

---

## The `this` Pointer

### Concept

Inside a non-static method, `this` is a pointer to the object that the method was called on.

### Explanation

When you write `a.takeDamage(10)`, the method needs to know which object's `health` to change. The compiler passes the address of `a` into the method as a hidden argument, and that is `this`.

It is most useful in two situations:

1. **Name conflicts**: when a parameter has the same name as an attribute, `this->name` refers to the attribute.
2. **Method chaining**: returning `*this` lets you call several methods on the same object in one line.

### Code (C++)

```cpp
class Player {
    string name;
    int score;

public:
    Player(string name, int score) {
        this->name = name;       // attribute = parameter
        this->score = score;
    }

    Player& addScore(int points) {
        score += points;
        return *this;            // return the same object
    }

    void show() const { cout << name << ": " << score << "\n"; }
};

int main() {
    Player p("Karim", 0);
    p.addScore(10).addScore(5).show();   // Karim: 15
}
```

---

## Object Lifecycle: Constructors and Destructors

### Concept

Every object is created, used, and destroyed. A **constructor** runs when it is created. A **destructor** runs automatically when it is destroyed. The destructor has the same name as the class with a `~` in front, takes no parameters, and cannot be overloaded.

### Explanation

The destructor is where an object cleans up after itself: closing files, releasing memory, disconnecting from something. C++ builds on this idea and calls it RAII (Resource Acquisition Is Initialization): a resource is acquired in the constructor and released in the destructor, so cleanup happens automatically and cannot be forgotten.

Rules for the order:

- Objects are destroyed in the **reverse** order of creation.
- With inheritance, the parent constructor runs first and the child destructor runs first.
- A local object is destroyed when the scope (the closing brace) it was created in ends.

### Code (C++)

```cpp
class Resource {
    string name;
public:
    Resource(string n) : name(n) { cout << name << " created\n"; }
    ~Resource()                  { cout << name << " destroyed\n"; }
};

int main() {
    Resource a("A");
    {
        Resource b("B");
    }                            // B is destroyed here
    Resource c("C");
}
// Output:
// A created
// B created
// B destroyed
// C created
// C destroyed
// A destroyed
```

---

## Stack vs. Heap

Objects can live in two different areas of memory.

| | Stack | Heap |
|---|---|---|
| How it is created | Normal declaration: `Player p("Karim");` | `new`: `Player* p = new Player("Karim");` |
| Lifetime | Until the end of its scope | Until you delete it |
| Cleanup | Automatic | Manual (`delete`) |
| Speed | Very fast | Slower |
| Size | Limited | Large |
| Typical use | Small, short-lived objects | Large objects, or objects that must outlive the scope that created them |

```cpp
Player p1("Karim");                    // stack: destroyed automatically
Player* p2 = new Player("Sara");     // heap: lives until deleted
p2->show();
delete p2;                           // must be done manually
```

Forgetting `delete` causes a **memory leak**. Deleting twice, or using the object after deleting it, causes undefined behavior. Modern C++ also has smart pointers that call `delete` for you, but they are outside the scope of this summary.

---

## Summary

- `static` members belong to the class and are shared by all objects. Static methods have no `this`.
- `this` points to the current object and enables name disambiguation and method chaining.
- Constructors initialize and destructors clean up. Destruction happens in reverse order of creation.
- Stack objects clean up automatically. Heap objects need `delete`.
