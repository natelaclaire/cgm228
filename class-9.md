---
layout: default
title: Class 9, Chapter 5
nav_order: 6
---

# Class 9, Chapter 5

---

## **Lecture Talking Points: Chapter 5 - Text and User Interfaces**

### 1. **Introduction to UI in LibGDX**

* Purpose of UI in games: Display information, interact with players.
* Overview of components covered:

  * **Labels** for text.
  * **Buttons** (image-based and text-based).
  * **Tables** for layout management.
  * Advanced UI: **Dialog Boxes**, **Cutscenes**, and **Visual Novels**.

---

### 2. **Displaying Text with Labels**

* Use of **Label** and **LabelStyle** in LibGDX.
* Importance of consistent design: Define styles in the **BaseGame** class.
* **BitmapFont**:

  * Bitmap vs. Vector fonts.
  * Two ways to create bitmap fonts:

    * **Hiero tool** (external editor).
    * **FreeTypeFontGenerator** (runtime, flexible).
* Example: Setting up a label to show remaining starfish.

---

### 3. **Creating Buttons**

* Types of buttons:

  * **Image-Based Buttons** (e.g., restart level).
  * **Text-Based Buttons** (e.g., Start, Quit).
* Using **ButtonStyle** and **TextButtonStyle**.
* **NinePatch** images to avoid distortion when scaling buttons.
* Handling button clicks:

  * **EventListener** and **Lambda Expressions**.
  * Benefits of lambdas for concise event handling.

---

### 4. **Organizing UI with Tables**

* Why manual positioning is inefficient.
* Introduction to **Table** class:

  * Rows, columns, and **Cell** management.
  * Methods: `add()`, `row()`, `pad()`, `expandX()`, `expandY()`, `colspan()`.
* Refactoring UI layout using tables in **MenuScreen** and **LevelScreen**.

---

### 5. **Dialog Boxes and Signs**

* Purpose: In-game tutorials, hints, NPC conversations.
* Building a reusable **DialogBox** class.
* Implementing signs that trigger dialog when the player is nearby.
* New method in **BaseActor**: `isWithinDistance()` for proximity detection.

---

### 6. **Cutscene Framework**

* Role of cutscenes in storytelling.
* Core components:

  * **SceneSegment**: Pairs an actor with an action.
  * **Scene**: Manages sequence of segments.
  * Custom actions: **SetTextAction**.
* Example: Starfish Collector cutscene flow.
* Handling player input to advance scenes.

---

### 7. **Game Project: Visual Novel - The Missing Homework**

* Introduction to visual novels as a genre.
* Game structure:

  * Branching story with player choices.
  * Use of existing UI and cutscene framework.
* New elements:

  * **TypewriterAction** for text effects.
  * Character emotions via **SetAnimationAction**.
  * Button-driven navigation through story branches.
* Discussion: How to expand this project (more locations, story depth).

---

### 8. **Key Concepts Recap**

* UI Elements: Labels, Buttons, Tables.
* Event handling with lambda expressions.
* Dialog systems and cutscenes.
* Flexibility of LibGDX for different game genres.
* Encouragement to customize UI and expand projects.

---

### 9. **Next Steps**

* Ideas for extending Starfish Collector and The Missing Homework.
* Preview of next chapter: Adding **audio** (music & sound effects).

---
