---
layout: default
title: Class 1, Chapter 1
nav_order: 2
---

# Class 1, Chapter 1

---

## **1. Introduction to Java Game Development with LibGDX**

* Overview of LibGDX: A cross-platform game development framework.
* Importance of using frameworks to simplify game development (reusability, efficiency).
* Today's goal: Set up the environment and understand your first LibGDX project.

---

## **2. Review of Basic Java Concepts**

### **Object-Oriented Programming (OOP)**

* **Classes & Objects**: Blueprints and instances.
* **Fields & Methods**: Variables and functions inside classes.
* **Access Modifiers**: `public`, `private`, etc.
* **Inheritance**:

  * Using `extends` to build on existing classes.
  * Example: `HelloWorldImage extends Game`.
* **Static Methods**:

  * Belong to the class, not instances.
  * The role of `public static void main(String[] args)` as the program entry point.

### **Java Development Basics**

* **Compilation & Execution**: Source code → Bytecode → JVM.
* **Java Libraries & JAR Files**: Bundles of reusable code.
* **Error Types**:

  * **Syntax Errors**: Caught at compile time.
  * **Runtime Errors**: Emerge during execution (e.g., missing files).

---

## **3. Setting Up the Development Environment**

### **Choosing an IDE**

* Options: BlueJ (beginner-friendly), Eclipse, IntelliJ, NetBeans (professional-grade).
* For this course: Starting with BlueJ for simplicity.

### **Installing BlueJ & JDK**

* Importance of the Java Development Kit (JDK).
* BlueJ setup steps:

  1. Download/install BlueJ (with or without bundled JDK).
  2. Create a new project and class.

---

## **4. Writing Your First Java Program**

### **Classic "Hello, World!"**

* Purpose: Test setup, introduce syntax.
* Key structure:

  ```java
  public class HelloWorld {
      public static void main() {
          System.out.print("Hello, World!");
      }
  }
  ```
* Using BlueJ:

  * Creating classes.
  * Writing, compiling, and running code.
  * Features: Syntax highlighting, auto-formatting, debugging tools.

---

## **5. Setting Up LibGDX in BlueJ**

* What is a software library? (Prewritten code to avoid reinventing the wheel.)
* LibGDX delivered as JAR files.
* Two ways to link JAR files in BlueJ:

  1. **+libs Folder** (per project).
  2. **userlib Directory** (global use).

---

## **6. Creating a LibGDX "Hello, World!"**

### **Shift from Text to Graphics**

* Instead of printing text, display an image.
* Introduction to core LibGDX classes:

  * **Game**: The base class for games.
  * **Texture**: Stores image data.
  * **SpriteBatch**: Draws images.
  * **Gdx**: Utility class for file and graphics handling.

### **Code Breakdown**

* **HelloWorldImage Class**:

  * Extends `Game`.
  * Uses `create()` for setup and `render()` for drawing.
* **Driver Class (HelloLauncher)**:

  * Launches the game using `LwjglApplication`.

---

## **7. Key Java & LibGDX Concepts Highlighted**

* **Inheritance in Practice**: Extending LibGDX’s `Game` class.
* **Event Loop**: `render()` method called \~60 times per second.
* **Static Methods**: Why `main` is static in launcher classes.
* **File Handling**: Using `Gdx.files.internal()`.

---

## **8. Common Errors and Debugging**

* Syntax issues (e.g., mistyping `print`).
* Runtime errors (e.g., missing image files).
* Fixing OpenGL context errors by resetting the JVM in BlueJ.

---

## **9. Advantages of Using LibGDX**

* Cross-platform development (desktop, Android, etc.).
* Built-in support for:

  * 2D/3D graphics.
  * Audio.
  * Input handling.
  * UI components.
  * Integration with tools like Box2D, Tiled, and Spine.

---

## **10. Wrap-Up and Next Steps**

* You've set up your environment and built a basic LibGDX app.
* Understand the foundation: IDE setup, Java basics, LibGDX structure.
* Preview of what's next:

  * Animations.
  * User input.
  * Game loops and logic.

---
