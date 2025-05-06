---
layout: default
title: Class 7, Chapter 4
nav_order: 5
---

# Class 7, Chapter 4

---

## 🎮 Introduction to Space Rocks

* **Overview**: Inspired by *Asteroids*, player controls a spaceship, destroys rocks with lasers.
* **Core Mechanics**:

  * Top-down view with screen wraparound.
  * Rotation, acceleration, minimal deceleration.
  * Laser shooting, shields, and teleportation.
* **Game Design Planning**: Importance of a game design document before coding.

---

## 🖥️ Setting Up the Project

* **Project Initialization**:

  * Create project in BlueJ.
  * Organize `assets` and `+libs` folders.
  * Reuse framework classes: `BaseGame`, `BaseScreen`, `BaseActor`.
* **Framework Extension**: Building on previous chapter's codebase.

---

## ⌨️ Handling Discrete Input

* **Continuous vs. Discrete Actions**:

  * Continuous: movement (holding keys).
  * Discrete: shooting, teleporting (single key press).
* **LibGDX InputProcessor**:

  * 8 required methods (keyboard, mouse, touchscreen).
* **InputMultiplexer**:

  * Combine `Stage` and `BaseScreen` for input handling.
  * Modify `BaseGame` and `BaseScreen` to support discrete input events.

---

## 🚀 Spaceship Implementation

* **Spaceship Class**:

  * Rotation, acceleration, and physics setup.
  * Screen wraparound logic via `wrapAroundWorld()`.
* **Visual Feedback**:

  * **Thrusters** using `Group` to sync visuals with movement.
  * **Shields** with pulsing animation and opacity for shield strength.
* **Teleportation**:

  * `Warp` effect triggered by X key.
  * Random repositioning logic.

---

## 🔫 Lasers, Rocks, and Explosions

* **Laser Class**:

  * Fires in facing direction, fades after 1 second.
* **Rock Class**:

  * Randomized speed and rotation.
  * Wraparound behavior.
* **Explosion Effect**:

  * Triggered on collisions.
  * Animation auto-removes itself.

---

## ⚡ Collision Handling & Game Logic

* **Interactions**:

  * Laser hits rock: both destroyed.
  * Rock hits spaceship:

    * If shields active: shield power reduced.
    * If shields depleted: spaceship destroyed.
* **Edge Case**:

  * Move destroyed spaceship off-screen to avoid collision checks.

---

## 🏆 Endgame Conditions

* **Lose Condition**: Spaceship destroyed when shields = 0.
* **Win Condition**: All rocks destroyed.
* **Display Messages**:

  * "Game Over" or "Congratulations" with fade-in effect.
* **Use of `gameOver` flag** to stop further updates.

---

## 💡 Summary & Possible Enhancements

* **Key Learnings**:

  * Handling discrete input.
  * Expanding reusable game frameworks.
  * Visual feedback for better player experience.
* **Suggested Improvements**:

  * Balance gameplay: adjust rock count, speed, or laser firing rate.
  * Add features:

    * Rock splitting (Asteroids-style).
    * Enemy UFOs.
    * Power-ups for shield restoration.
  * Implement a start menu.

---

## ➡️ Next Steps

* Preview of next chapter: Focus on UI design and displaying text in games.
