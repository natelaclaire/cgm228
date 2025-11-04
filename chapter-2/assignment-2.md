**Assignment 2: Exploring and Modifying the Starfish Collector Game**

---

### **Objectives**

By completing this assignment, you will:

1. Reinforce your understanding of:  
   * The game loop and how `act()` and `draw()` methods function in LibGDX.  
   * Managing actors and stages in a LibGDX project.  
   * Collision detection and game-ending feedback.  
2. Learn to extend and modify existing game functionality.  
3. Practice iterative development and debugging.  
4. Gain experience with version control using GitHub.

---

### **Steps**

#### **1\. Read Chapter 2 of the Textbook**

* Chapter 2 covers critical concepts, including:  
  * The structure of a LibGDX project.  
  * The life cycle of a game, including the game loop (`act()`, `update()`, `draw()`).  
  * Managing actors and stages.  
* Focus on the collision detection examples and how actors are added to the stage.

#### **2\. Explore the Starfish Collector Game**

1. Clone the GitHub repository provided in Brightspace containing the Starfish Collector game.  
2. Unlike the last repository, this one contains three different branches, each representing a different version of the Starfish Collector game:  
   * `alpha`  
   * `beta`  
   * `gamma`  
3. Using the Current Branch button in GitHub Desktop, switch to the `alpha` branch.
4. Open the `starfish-collector` project in Android Studio.
5. Explore the project structure and familiarize yourself with the codebase.  
   * Identify where the main game loop is implemented.  
   * Review how the textures are loaded and managed.
   * Review how keypresses are handled.
6. Create an Application run configuration as we did last time and run the game, using the arrow keys on the keyboard to move the turtle around the screen to collect starfish and reach the winning state.
7. Switch to each of the other branches (`beta` and `gamma`) one at a time, exploring how the code differs and running the game to see if there are differences in behavior.
   * Alpha: Initial game with basic actor and stage setup.  
   * Beta: Refactored code with improved organization and a generic `GameActor` class that can be extended.  
   * Gamma: Includes game flow logic and basic collision detection.  

#### **3\. Modify the Final Version**

Using GitHub Desktop, switch to the `gamma` branch. This is the most complete version of the game. Your task is to add a new feature: a shark that moves across the screen and ends the game if it collides with the turtle. Before you begin, create a new branch from `gamma` named `feature/shark-collision`.

##### **3.1 Add the Shark Actor**

1. Create a new `Shark` class:  
   * Ensure the `Shark` class extends `GameActor`, similar to the `Turtle` class.  
   * Load the `sharky.png` graphic as the shark's texture.
   * Set up the `Shark` actor with a polygon boundary for collision detection.  
2. Add the `Shark` actor to the stage in the `initialize()` method of `StarfishCollector`.  
   * Place the shark off-screen initially so it moves onto the screen during gameplay.

##### **3.2 Implement Shark Movement**

1. In the `Shark` class, add logic to move the shark in a single direction (e.g., left to right) at one pixel per frame.  
   * Example: Use `moveBy()` within the `act()` method to update the shark’s position.  

##### **3.3 Add the "Game Over" Message**

1. Create a new `BaseActor` object in the `update()` method for the "Game Over" graphic.  
   * Use `setOpacity()` to fade in the message if desired.  
   * Position the graphic at the center of the screen.

##### **3.4 Add Collision Detection**

1. In the `update()` method of `StarfishCollector`, check for overlaps between the `Shark` and `Turtle` actors:  
   * Use the `overlaps()` method from `GameActor`.  
   * If a collision occurs, execute the following:  
     * Remove the `Turtle` actor from the stage.  
     * Display the `game-over.png` graphic using the object created in 3.3.

#### **4\. Test Your Changes**

1. Run the modified game.  
2. Verify the following:  
   * The shark moves visibly across the screen.  
   * The collision logic works, and the turtle is removed upon collision.  
   * The "Game Over" graphic is displayed correctly.  
3. Use the following checklist:  
   * Does the shark move at the intended speed and direction?  
   * Is the turtle removed immediately upon collision?  
   * Is the "Game Over" message displayed promptly and clearly?

#### **5\. Commit and Push Your Changes**

1. Use GitHub Desktop to commit your changes:  
   * Ensure all modified files and assets (`sharky.png`, `game-over.png`) are included in the commit.  
   * Write a clear commit message (e.g., "Added Shark actor with collision logic and Game Over graphic").  
2. Push your changes to your GitHub repository.

#### **6\. Submit Your Assignment**

1. Navigate to Brightspace and locate the Week 2 submission link.  
2. Submit the URL to your GitHub repository.  
3. In the comment box, include a brief description of your modifications (e.g., "Added Shark actor with collision logic and implemented Game Over functionality").

---

### **Optional Extensions**

If you have extra time, consider enhancing the game with the following features:

1. **Randomized Starting Position**:  
   * Have the shark start at a random position off-screen for each game session.  
2. **Directional Variety**:  
   * Implement logic for the shark to move toward the turtle’s position.  
3. **Restart Functionality**:  
   * Add a key press event to restart the game after the "Game Over" message appears.

---

### **Grading Criteria**

Your assignment will be graded based on the following:

| Criteria | Weight |
| ----- | ----- |
| Shark actor added correctly | 20% |
| Shark movement implemented | 20% |
| Collision detection and logic | 30% |
| Game Over graphic displayed | 20% |
| Code organization and clarity (includes documenting the code properly with comments and helpfully descriptive variable names) | 10% |

---

### **Troubleshooting Tips**

1. **Actor Not Visible**:  
   * Ensure the shark's position is within the screen bounds.  
   * Verify the graphic is correctly loaded using the `setTexture()` method.  
2. **Collision Not Detected**:  
   * Check that both actors have their boundary polygons set up correctly.  
   * Use debug tools or log statements to verify actor positions and boundaries.  
3. **Game Over Graphic Not Displaying**:  
   * Verify the graphic is added.  
   * Ensure `setVisible(true)` or `setOpacity()` is used if needed.

This assignment builds on the foundational concepts in Chapter 2, providing a structured and hands-on approach to learning game development with LibGDX. Good luck and have fun coding\!
