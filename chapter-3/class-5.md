---
layout: default
title: Class 5, Chapter 3
nav_order: 4
---

# Class 5, Chapter 3

---

## **Lecture Talking Points: Chapter 3 – Extending the Framework**

### **1. Identifying Game Shortcomings**

* Recap the limitations of the initial Starfish Collector game:

  * No animations, rough movement, imprecise collisions.
  * No obstacles, only one collectible, limited game world.
  * No start menu—game starts immediately.

### **2. Introducing the `BaseActor` Class**

* Explain the creation of `BaseActor`:

  * Replaces `ActorBeta` for a more robust, reusable foundation.
  * Centralizes common functionality (animations, movement, collisions).
  * Discuss trade-offs of combining features in one class vs. strict OOP design.

### **3. Adding Animations**

* **Value-Based Animations**:

  * Using LibGDX `Action` class for effects like rotation, movement, scaling, fading.
  * Example: Starfish rotates using `Actions.rotateBy`.
* **Image-Based Animations**:

  * Using `Animation<TextureRegion>` for frame-based animations.
  * Loading from multiple files or spritesheets.
  * Show methods: `loadAnimationFromFiles` and `loadAnimationFromSheet`.

### **4. Implementing Physics-Based Movement**

* Concepts of **velocity** and **acceleration** using `Vector2`.
* Methods:

  * `setSpeed`, `setMotionAngle`, `accelerateAtAngle`, `applyPhysics`.
* Discuss handling deceleration and maximum speed.
* Demo smooth movement vs. instant movement.

### **5. Precise Collision Detection**

* Difference between rectangles and polygons for collisions.
* Using LibGDX `Polygon` and `Intersector` classes.
* Method: `overlaps` for detecting collisions.
* Show how to simulate solid objects with `preventOverlap`.

### **6. Managing Multiple Game Objects**

* Using `ArrayList` to handle multiple instances (rocks, starfish).
* Static helper methods in `BaseActor`:

  * `getList` and `count` for dynamic object management.

### **7. Expanding the Game World**

* Setting **world boundaries**:

  * `setWorldBounds` and `boundToWorld` methods.
* Implementing camera scrolling:

  * `alignCamera` keeps player centered while respecting world edges.
* Difference between game world and visible window.

### **8. Separating Game Logic and UI**

* Introduction of a second stage: `uiStage` for HUD and messages.
* Keeping UI elements like "You Win" fixed on screen.

### **9. Supporting Multiple Screens**

* Refactoring with `BaseGame` and `BaseScreen`:

  * Easier management of menus, levels, and transitions.
* Example: `MenuScreen` and `LevelScreen`.
* Use of `setActiveScreen` for switching screens.

### **10. Summary and Best Practices**

* Importance of building reusable frameworks.
* Encouragement to expand the game:

  * Add more levels, obstacles, enemies, or UI features.
* Highlight upcoming topics: UI, sound, level design.

---
