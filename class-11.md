---
layout: default
title: Class 11, Chapter 6
nav_order: 7
---

# Class 11, Chapter 6

---

## **Lecture Talking Points: Chapter 6 – Audio in LibGDX**

### **1. Introduction to Audio in Games**

* Importance of audio: Enhances immersion with sound effects (SFX) and background music.
* LibGDX audio support:

  * File formats: MP3, OGG, WAV.
  * Two main interfaces: `Sound` (short effects) vs. `Music` (longer tracks, streamed).

### **2. Using the `Sound` Interface**

* For short sound effects (<1MB).
* Example of loading and playing:

  ```java
  Sound effect = Gdx.audio.newSound(Gdx.files.internal("beep.wav"));
  effect.play(1.0f);  // Full volume
  ```
* Supports overlapping playback.

### **3. Using the `Music` Interface**

* For background music or ambient sounds (files >1MB).
* Example of loading and controlling music:

  ```java
  Music song = Gdx.audio.newMusic(Gdx.files.internal("song.mp3"));
  song.setLooping(true);
  song.play();
  ```
* Methods: `play()`, `pause()`, `stop()`, `setVolume()`, `setLooping()`.
* Always call `dispose()` when done to free resources.

### **4. Practical Example: Adding Audio to Starfish Collector**

* Steps:

  * Load sound and music files.
  * Play sound effect when collecting items.
  * Loop background music.
  * Add mute/unmute button using UI controls.
  * Toggle volume using `audioVolume = 1 - audioVolume`.
* Reminder: Manage memory with `dispose()` on restart.

---

## **5. Advanced Project: Rhythm Tapper Game**

* Genre: Rhythm action game (e.g., DDR, Guitar Hero).
* Core mechanic: Press F, G, H, J keys in sync with falling boxes and music beats.
* UI Elements:

  * Start button.
  * Time and score display.
  * Feedback messages ("Perfect", "Great", etc.).

### **6. Handling File Operations in LibGDX**

* Use `FileHandle` for cross-platform file management.
* Reading timing data:

  ```java
  String[] lines = handle.readString().split("\n");
  ```
* Writing data with `writeString()`.

### **7. JavaFX File Chooser Integration**

* Why: LibGDX lacks built-in file dialogs.
* Solution: Use JavaFX `FileChooser` via a utility class (`FileUtils`).
* Handle threading with `Platform.runLater()`.

---

## **8. Recording Rhythm Data**

* Use a custom `RecorderScreen` to:

  * Load music.
  * Record keystrokes in sync with playback.
  * Save timing data to a text file.
* Data stored as key-time pairs in `SongData` class.

### **9. Building Rhythm Tapper Gameplay**

* Lists to manage:

  * Keys (`F`, `G`, `H`, `J`).
  * Target boxes and falling boxes.
* Synchronize falling boxes with beats using a lead time (3 seconds).
* Score system based on timing accuracy.

---

## **10. Enhancing User Experience**

* Countdown before song starts (visual + sound cues).
* End-game "Congratulations" message.
* Visual effects:

  * Pulse effect on targets.
  * Fade-out animation on falling boxes.
* Feedback for missed notes.

---

## **11. Best Practices and Tips**

* Always manage audio resources properly (`dispose()`).
* Use clear data structures for rhythm games (e.g., `ArrayList` for timing data).
* Integrate UI for better usability (mute buttons, score display).
* Consider adding:

  * More sound effects.
  * Post-game stats (e.g., % accuracy, message counts).

---

## **12. Summary**

* Key takeaways:

  * How to implement `Sound` and `Music` in LibGDX.
  * File handling with `FileHandle` and JavaFX dialogs.
  * Building an interactive rhythm game.
* Encourage experimenting with adding audio to previous projects (e.g., Space Rocks).
