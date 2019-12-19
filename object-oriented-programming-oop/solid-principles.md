---
description: 'Reference: https://www.baeldung.com/solid-principles'
---

# SOLID Principles

So, what is SOLID and how does it help us write better code? Simply put, Martin's and Feathers' **design principles encourage us to create more maintainable, understandable, and flexible software**. Consequently, **as our applications grow in size, we can reduce their complexity** and save ourselves a lot of headaches further down the road!

**S - Single responsibility principle**

This principle states that **a class should only have one responsibility. Furthermore, it should only have one reason to change.** How does this principle help us to build better software? Let's see a few of its benefits:

1. **Testing** – A class with one responsibility will have far fewer test cases
2. **Lower coupling** – Less functionality in a single class will have fewer dependencies
3. **Organization** – Smaller, well-organized classes are easier to search than monolithic ones

**O - Open / closed principle**

Simply put, **classes should be open for extension, but closed for modification.** **In doing so, we** **stop ourselves from modifying existing code and causing potential new bugs** in an otherwise happy application. Of course, the **one exception to the rule is when fixing bugs in existing code.** We can make sure that our code is compliant with the open/closed principle by utilizing inheritance and/or implementing interfaces that enable classes to polymorphically substitute for each other.

**L - Liskov substitution principle**

Simply put, **if class** _**A**_ **is a subtype of class** _**B**_**, then we should be able to replace** _**B**_ **with** _**A**_ **without disrupting the behavior of our program.** More generally it states that objects in a program should be replaceable with instances of their subtypes without altering the correctness of that program.

**I - Interface segregation principle**

it simply means that **larger interfaces should be split into smaller ones. By doing so, we can ensure that implementing classes only need to be concerned about the methods that are of interest to them.**

**D - Dependency inversion principle**

The principle of Dependency Inversion refers to the decoupling of software modules. This way, instead of high-level modules depending on low-level modules, both will depend on abstractions and, Abstractions should not depend on details, the details should depend on abstractions.

