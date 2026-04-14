## Programming Paradigms Overview

**Why do we even need paradigms?**
- To manage the chaos (complexity) of big projects.
- To help us write better, cleaner code.
- To avoid "non-essential complexity" (basically, the mess we create ourselves when we use the wrong tools or write spaghetti code).
- **The Goal:** Code should always be:
  - Simple (if I need a paragraph of comments to explain it, it's too complex).
  - Reusable.
  - Readable.
  - Easy to change later.

**What exactly is a Programming Paradigm?**
- It's basically a specific style or approach to writing code. It uses a strict set of rules or constraints to make complex software easier to write, read, maintain, and reuse.
- **Common Examples:**
  - Structured
  - Object-Oriented Programming (OOP)
  - Functional
  - Procedural
  - Logical
  - Reactive

**How Languages handle Paradigms**
- Most programming languages support one or more of these styles.
- Languages give you specific built-in features to make writing in that style super easy.
- They also purposely *leave out* features that would break the rules of that specific paradigm.

**Structured Programming**
- The classic way of writing code using basic flow-control structures.
- Examples of these structures:
  - Conditionals (if/else)
  - Loops (for/while)
  - Function calls and returns
  - Try/catch blocks
 
  - jump to anyline of code using line number or label
 - <img width="629" height="191" alt="image" src="https://github.com/user-attachments/assets/bc80e56b-78db-4b98-b40f-acff5e516f2e" />
 ## Structured Programming (Life after GOTO)

- Before structured programming, developers used `GOTO` statements to jump around the code. 
- While `GOTO` gave you total power, it quickly created messy, complex "spaghetti code".
- Structured programming took away that chaotic power and replaced it with clean, predictable structures (like loops and conditionals) to keep the code organized.

## Object-Oriented Programming (OOP)

- **The core idea:** Everything is treated as an "Object".
- A program is just a bunch of related objects communicating with each other to get tasks done.

**The Main Concepts:**
1. **Classes & Objects:** Objects bundle their data (**state** / instance variables) and their actions (**behavior** / methods) together in one place.
2. **Inheritance:** You can share code by creating family trees (hierarchies). A child class inherits traits from its parent.
3. **Polymorphism:** You can call the *exact same method* on different sub-types, and they will each execute it in their own unique way.

** before OOP Languages:**
- You *could* write object-oriented code in older, non-OOP languages, but it required extreme discipline. 
- You had to manually group methods and variables, manually pass parameters to fake relationships, and rely purely on convention. The language didn't enforce anything.
- **Why OOP languages matter:** They have built-in syntax and strict rules that *enforce* these concepts, so you don't have to do the heavy lifting manually.

**The real power of OOP:** - It lets us tackle much harder problems without drowning in complexity. The language handles the heavy lifting of enforcing the rules, so we can just focus on writing the code.

**When OOP Shines (The Rule of Thumb):**
- It's perfect when you have **many things** (objects) but a **fixed set of operations** (methods).
- **Easy:** Adding or removing "things" (you just add/remove a class).
- **Hard:** Adding or removing "operations" (you have to go in and manually update the methods across *many* different classes).

---

## Functional Programming (FP)

- **The core idea:** Write code using **pure functions** as much as possible and strictly manage your "side effects".
- It's actually really hard to build an entire app using *only* pure functions, so FP languages have built-in features to help enforce and manage this style for you.

**Pure Functions & Side Effects**
- A **pure function** is simple: it relies *only* on the parameters you give it, and it has absolutely ZERO side effects.
- A **side effect** is when a function does literally *anything* other than just returning a value. 
  - *Examples:* Printing to the screen, sending an email, updating a database, or modifying an outside instance variable.
- *Why are side effects a problem?* Because sometimes you call a function just expecting it to calculate a value, and it secretly updates a database in the background and breaks something else.

**Immutability (Data cannot change)**
- In FP, data is immutable. 
- If you need to "update" or change data, you don't modify the original variable. Instead, you create a brand new copy of the data with the changes applied.

**Two Types of FP Languages:**
1. **"Pure" Functional Languages:** Clojure, Common Lisp, Scheme, Elixir, Erlang, F#, Haskell, OCaml. *(These strictly enforce FP rules).*
2. **Languages that just support a "Functional Style":** C++, C#, Go, Java, JavaScript, Kotlin, PHP, Python, Rust, Scala, Swift. *(You can write FP in these, but the language won't force you to).*

 ## First-Class Functions

- In functional programming, functions are treated exactly like regular values.
- Because they are just values, you can:
  - Assign them to variables.
  - Pass them as arguments into other functions.
  - Return them as outputs from other functions.

**Higher-Order Functions**
- Simply put: It's any function that either *takes* another function as a parameter, or *returns* another function as a result.

**When FP Shines (The Rule of Thumb):**
- It's perfect when you have **many operations** that work with a **fixed set of things** (this is the exact opposite of OOP).
- **Easy:** Adding or removing operations (you just add/remove a function).
- **Hard:** Adding or removing "things" (you have to go through and update the parameters on *many* different functions).

---

## Data, Calculations, and Actions

- **Calculations:** These are your pure functions (they just take inputs, do the math/logic, and return a value with zero side effects).
- **Actions:** These are your impure functions (they have side effects, like talking to a database, writing to a file, or updating the screen).
- **The Golden Rule:** Keep your "actions" as absolutely simple and small as possible.

## The Core of Functional Programming: Actions, Data, and Calculations

**1. ACTIONS **
- **Definition:** Any instruction where the *time* and *order* it is called actually matters.
- They have side effects (calling them changes something in the system).
- You have to be super careful with them, but a program *needs* actions (you can't build an app with ONLY pure functions; it has to actually *do* something eventually).
- **How to handle them:** - Find ways to safely change state over time.
  - Guarantee the order they run in.
  - Ensure specific actions only happen once.
- *(Note: Data and Calculations don't care when they are called because they just accept inputs and return outputs without changing the system).*

**2. DATA **
- **Definition:** Just facts about events. Data itself does no actual work.
- **Types:**
  - *Immutable:* Cannot be changed after it is initialized.
  - *Mutable:* Can be changed after it is initialized.
- **The Rule:** Functional programming tries to use **Immutable** data as much as humanly possible.
- **Techniques:** Organize it for efficient access, establish disciplines for storing it, and figure out exactly what is important to capture.

**3. CALCULATIONS **
- **Definition:** Pure computation from input to output.
- These are your **pure functions**. They have absolutely zero side effects.
- If you give it the exact same input, it will ALWAYS produce the exact same output.
- *Getters vs Setters:* `Getters` are pure functions (safe). `Setters` are NOT pure (they are actions) because they change the state of a variable.
- **Referential Transparency:** A fancy term meaning you could completely replace the function call in your code with its final returned value, and the program wouldn't change at all. Calculations are referentially transparent.
- **Why we prefer Calculations over Actions:**
  - They are highly composable (easy to chain together).
  - IDEs can automatically analyze them and check for correct usage.
  - They are incredibly easy to test compared to actions.



#### Data > Calculations > Actions

All three categories are useful but:
- Prefer **DATA** over both, calculations and actions
  - **IMMUTABLE** data over mutable data
- **CALCULATIONS** over actions
- **ACTIONS** should be as stupid as possible, so that just by looking at the code you can tell if it is doing the right thing or not\

-- Simpler actions, data and calculations can hide in complex actions. -- 
## The Architecture: Functional Core vs. Imperative Shell

To build a clean functional app, we split it into two distinct parts:

**1. The Functional Core (The Brain)**
- Contains **100% of the app's logic**.
- Made entirely of immutable data and pure functions.
- Completely isolated. It has NO idea the "messy outside world" exists (no databases, no network calls, no files).

**2. The Imperative Shell (The Bouncer)**
- Contains almost **zero logic** (it delegates all the smart stuff to the core).
- It sequences operations (decides the order of what happens).
- It talks to the "messy outside world" (fetches from the database, prints to the screen).
- **Its main job:** Coordinate data between the outside world and the functional core.

---

## Data Types in Java (FP Style)

**Records (Data Classes)**
- Purely used to represent a data type.
- They are just containers that hold information.
- They do **not** contain methods (behavior).

**Enums**
- Represent a specific, fixed set of values (e.g., `NORTH, SOUTH, EAST, WEST`).
- Way better than using plain Strings because the compiler will catch errors if you type an invalid value.

**Sealed Interfaces**
- Just like a normal interface (forces implementing classes to have specific methods), BUT with a strict lock on it.
- **The catch:** You explicitly define *exactly which classes* are allowed to implement it. 
- *Syntax example:* `public sealed interface Shape permits Circle, Square {}`
- Because the allowed subtypes can be completely different from each other, it's very common to just define nested Records (data types) inside them instead of a bunch of methods.

---

## Inputs and Outputs (Explicit vs. Implicit)

**Inputs (What goes in)**
- **Explicit Input:** Just the normal **Parameters** passed into the function.
- **Implicit Input:** Sneaky inputs. Things the function grabs from the outside world (global variables, reading a file, asking for user input).

**Outputs (What comes out)**
- **Explicit Output:** Just the normal **Returned value**.
- **Implicit Output:** Sneaky side effects. (e.g., printing to a screen, saving to a database, or modifying the value of the parameter that was passed in).

---

## How to Clean Up Your Code (Extracting Calculations from Actions)

If you can't completely delete an action, you should at least improve it by minimizing its implicit inputs and outputs. 

**The 3-Step Refactoring Process:**
1. **Extract:** Find the hidden calculation inside the messy action and pull it out into its own separate subroutine.
2. **Identify:** Look at the new subroutine and spot all its implicit inputs and implicit outputs.
3. **Convert:** Turn the implicits into explicits.
   - *Outputs first:* Change implicit side-effects into explicit **Return values**.
   - *Inputs second:* Change implicit global reads into explicit **Parameters**.

**Dependency Injection:** - Instead of a function secretly grabbing the data it needs (implicit), you explicitly pass the data into it as a parameter (injecting the dependency). This creates **loosely coupled functions** that are easy to test.

---

## The Singleton Pattern
*(A quick Object-Oriented design pattern)*

- **The Goal:** Make sure a class only ever has **ONE** instance running in the entire app, and give a global access point to it.
- **The Setup:**
  1. A `private` class variable of the exact same type as the class itself.
  2. A `private` constructor (so nobody else can use `new` to create one).
  3. A `public` method (usually `getInstance()`) that calls the private constructor once, and just returns that same instance every time it's called.
