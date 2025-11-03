---
layout: default
title: Class 3, Chapter 2
nav_order: 3
---

# Class 3, Chapter 2

---

## **Talking Points for Lecture: LibGDX Framework (Chapter 2)**

### 1. **Introduction to LibGDX and Starfish Collector**

* Overview of LibGDX as a Java game development framework.
* Introduction to the **Starfish Collector** game as a practical example.
* Focus: Start simple, then refactor using object-oriented principles and LibGDX features.

---

### 2. **Game Life Cycle in LibGDX**

* **Four Main Stages**:

  * **Startup** (`create()`): Load assets, initialize objects.
  * **Game Loop** (`render()`):

    * Process Input
    * Update Game State
    * Render Graphics
  * **Shutdown** (`dispose()`): Free resources, save data.
* LibGDX enforces this flow via interfaces like `ApplicationListener`.
* Note: LibGDX handles timing (60 FPS target) and background tasks like sleeping.

---

### 3. **Java Interfaces in Game Development**

* Concept of **Interfaces** as contracts (e.g., `ApplicationListener`).
* Example: The `Speaker` interface and how multiple classes implement shared behavior.
* How LibGDX uses interfaces to manage game life cycle methods.
* Explain why extending classes like `Game` simplifies development (pre-implemented methods).

---

### 4. **Building the First Game: StarfishCollectorAlpha**

* Basic game setup:

  * Control a turtle to collect a starfish.
  * Arrow key movement, collision detection using `Rectangle`.
  * Display "You Win" message upon success.
* Key Classes:

  * `Texture`, `SpriteBatch`, `Rectangle`, `Gdx.input`.
* Discuss the structure:

  * All logic inside `render()`.
  * Manual handling of drawing order and input processing.

---

### 5. **Improving Design: Actors and Stages**

* Introduction to **Actor** and **Stage** classes:

  * Encapsulate position, size, and behavior.
  * Stage manages multiple actors, simplifying draw and update logic.
* Creation of **ActorBeta**:

  * Custom actor with texture and collision detection.
* **Turtle Class**:

  * Extends ActorBeta to handle player input within `act()` method.
* Importance of **Object-Oriented Design**:

  * Encapsulation and reuse.
  * Cleaner, more scalable code.

---

### 6. **Refactoring Game Flow**

* Splitting tasks for clarity:

  * Separate **input processing**, **game state updates**, and **rendering**.
* Introduction of **GameBeta** class:

  * Base class to handle common framework tasks.
  * Use of `initialize()` and `update()` methods.
* Use of **abstract classes**:

  * Combine benefits of interfaces and base classes.
  * Enforce structure while allowing flexibility.

---

### 7. **Final Structure: StarfishCollectorBeta**

* Cleaner, modular design:

  * Game logic in `update()`.
  * Framework tasks handled by GameBeta.
  * Stage automates actor management.
* Example of removing redundancy and improving maintainability.
* Importance of draw order and visibility control.

---

### 8. **Best Practices Highlighted**

* Keep methods focused on single responsibilities.
* Use inheritance and abstraction to reduce code duplication.
* Leverage LibGDX’s built-in tools (`Stage`, `Actor`, `Batch`).
* Always think ahead: design for future scalability.

---

### 9. **Next Steps and Practice**

* Suggested Exercise: Add a **Shark** enemy.

  * If turtle overlaps shark, display “Game Over” and remove turtle.
* Prepare for next chapter:

  * Animation, better collision detection, physics, and handling multiple actors.

---
