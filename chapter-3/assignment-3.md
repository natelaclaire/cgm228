**Assignment 3: Extending the Starfish Collector Game**

---

### **Objectives**

By completing this assignment, you will:

1. Build upon the foundational knowledge from Chapters 1 and 2 to implement advanced features.  
2. Reinforce your understanding of:  
   * Animations and physics-based movement.  
   * Improved collision detection with polygons.  
   * Managing multiple actors and creating dynamic gameplay.  
3. Enhance your skills in iterative development and debugging.  
4. Gain experience implementing and testing reusable code for future projects.

---

### **Steps**

#### **1\. Read Chapter 3 of the Textbook**

* Chapter 3 introduces advanced features, including:  
  * Creating animations using `TextureRegion` and the `Animation` class.  
  * Physics-based motion with acceleration, velocity, and deceleration.  
  * Collision detection using polygons for better precision.  
  * Managing collections of actors dynamically.  
* Focus on the section about extending the `ActorBeta` class into a more robust `BaseActor` class.  

#### **2\. Explore the Starfish Collector Game**

1. Clone the GitHub repository provided in Brightspace containing the Starfish Collector game.  
2. Like last week, this repository contains multiple branches. Explore them in order:
   * `gamma` - the final version from Assignment 2 (without your changes).
   * `delta` - adds animations, physics-based movement, and multiple actors.
   * `epsilon` - adds multiple screen management and UI elements.
3. Using the Current Branch button in GitHub Desktop, switch to the `delta` branch.
4. Open the `starfish-collector` project in Android Studio.
5. Explore the changes that were implemented throughout the chapter.
6. Create an Application run configuration as we did last time and run the game, using the arrow keys on the keyboard to move the turtle around the screen to collect starfish and reach the winning state.
7. Switch to the `epsilon` branch, explore how the code differs, and run the game to see the differences in behavior.

#### **3\. Extend the Starfish Collector Game**

Using GitHub Desktop, switch to the `epsilon` branch. This is the most complete version of the game. Your task is to add two new features: random object placement and a second level that is more difficult than the first. Before you begin, create a new branch from `epsilon` named `feature/difficulty-scaling`.

##### **3.1 Randomize Object Placements**

Randomize the placement of the starfish and rocks, ensuring that it's possible for some of them to be placed beyond the initial viewport.

##### **3.2 Add a Second Level**

As described on page 81 of the textbook, add a second level that appears after the player collects all starfish and presses the C key, using the message-continue.png graphic between levels. Display the you-win.png file only if the player completes both levels. How you differentiate the levels is up to you, but you could consider having more sharks, more rocks, and/or more starfish in the second level. Another approach would be to have no shark for the first level and add the shark in the second level. Rock and starfish placements should be randomized for both levels.

##### **3.3 Adjust Shark Behavior and Super Class**

Speaking of sharks, you'll need to add your shark from the last assignment to the latest version of the project and modify your `Shark` class so that it extends the `BaseActor` class. Also consider: how will your shark(s) appear on the stage now that we have sand on all sides? Will they slide into the water from the beach (this is what happens if you don't change the logic)? Will they fade in from random locations in the water? You should probably ensure that they don't enter the scene too close to your turtle...

#### **4\. Test Your Changes**

1. Compile and run the modified game.  
2. Use the following checklist to verify functionality:  
   * The turtle displays a smooth swimming animation.
   * Rocks behave as solid obstacles.
   * The starfish rotates and is removed upon collection.
   * The whirlpool effect appears and disappears as expected.
   * The "Press C to Continue" message displays after all starfish are collected in level 1.
   * The second level is more challenging than the first.
   * The "You Win" message displays after all starfish are collected in level 2.

#### **5\. Commit and Push Your Changes**

1. Use GitHub Desktop to commit your changes:  
   * Include modified files and new assets.  
   * Write a clear commit message (e.g., "Added second level and random placement to the Starfish Collector game").  
2. Push your commits to your GitHub repository.

#### **6\. Submit Your Assignment**

1. Navigate to Brightspace and locate the Assignment 3 submission link.  
2. Submit the URL to your GitHub repository.  
3. In the comment box, include a brief description of your modifications (e.g., "Added second level and random placement to the Starfish Collector game").

---

### **Grading Criteria**

Your assignment will be graded based on the following:

| Criteria | Weight |
| ----- | ----- |
| Random object placement | 25% |
| Second level | 40% |
| Integration of Shark into new structure | 20% |
| Code organization and clarity (includes documenting the code properly with comments and helpfully descriptive variable names) | 15% |

---

### **Troubleshooting Tips**

1. **Animation Not Displaying**:  
   * Verify that the file paths for animation frames are correct.  
   * Ensure `elapsedTime` in `BaseActor` is being updated.  
2. **Collision Issues**:  
   * Check that boundary polygons are correctly set for all actors.  
   * Use debug tools to visualize polygons for troubleshooting.  
3. **Unexpected Behavior**:  
   * Use log statements to track actor positions, collisions, and animations.

This assignment deepens your understanding of game development concepts and prepares you for more complex projects later in the course. Good luck, and have fun coding!