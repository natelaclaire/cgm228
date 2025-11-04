**Assignment 1: Setting Up Your Development Environment**

---

### **Objectives**

By completing this assignment, you will:

1. Familiarize yourself with the tools and technologies for Java development:  
   * Setting up and configuring Java, Android Studio, and the LibGDX library.  
   * Managing repositories with GitHub.  
2. Run and modify simple Java programs to:  
   * Reinforce fundamental object-oriented programming (OOP) concepts.  
   * Experiment with the LibGDX library.  
3. Develop familiarity with version control and collaborative coding practices.

---

### **Steps**

#### **1\. Install Java**

1. Download and install **Java 17 or 21** from one of the following sources:  
   * Adoptium: [https://adoptium.net/](https://adoptium.net/) (Java LTS \- Long-Term Support \- is version 21.x, which is what we want)  
   * Oracle: [https://www.oracle.com/java/technologies/javase-downloads.html](https://www.oracle.com/java/technologies/javase-downloads.html)  
     **Note: if you use the Oracle link, you’ll need to switch from JDK 23 to JDK 21 before downloading**  
     **![][image1]**  
2. Verify your installation:  
   * Open a Terminal or Command Prompt.  
   * Run the command `java -version`.  
   * Confirm it outputs the installed Java version.

#### **2\. Install Android Studio (IDE) and the LibGDX Project Setup Tool (gdx-liftoff)**

1. Download and install Android Studio from [https://developer.android.com/studio](https://developer.android.com/studio).
2. During installation, ensure the option to install the **Android SDK** is selected.
3. Install the LibGDX Project Setup Tool (gdx-liftoff) by following the instructions at [https://libgdx.com/wiki/start/project-generation](https://libgdx.com/wiki/start/project-generation).

#### **3\. Read Chapter 1 of the Textbook**

* Familiarize yourself with the concepts in Chapter 1 of *Java Game Development with LibGDX*. This will guide you through setting up the Java development environment and running a basic LibGDX application, but note that it covers BlueJ, not Android Studio. There’s no need to follow along with the instructions in this chapter - we’ll be covering the Android Studio steps in this assignment and in class.

#### **4\. Create a GitHub Account**

* Sign up for a free GitHub account at [https://github.com/](https://github.com/).  
* (Optional) Students can also apply for the GitHub Student Developer Pack for additional tools and resources.

#### **5\. Join the Course GitHub Classroom**

* Accept the invitation to Assignment 1 in our GitHub Classroom via the provided link in Brightspace.  
* This will set up your personal repository for the assignment and include starter files.

#### **6\. Install GitHub Desktop**

1. Download and install GitHub Desktop from [https://desktop.github.com/](https://desktop.github.com/).  
2. Sign in with your GitHub credentials.  
3. Use GitHub Desktop to clone your repository:  
   * Navigate to your GitHub Classroom repository.  
   * Click the green **Code** button and select **Open with GitHub Desktop**.  
   * Choose a local folder for the repository and click **Clone**.

#### **7\. Run and Modify Provided Java Programs**

##### **7.1. HelloWorld.java**

1. In GitHub Desktop, go to Repository > Open in Command Prompt (or Terminal).
2. Type `cd 1.1-hello-world` and press Enter.
3. Type `javac HelloWorld.java` to compile the program.
4. Type `java HelloWorld` to run the program and verify it prints "Hello, World\!".
5. Open the `HelloWorld.java` file in a text editor (e.g., Notepad, VS Code).
6. Modify the program to display a custom message, such as "Hello, \[Your Name\]\!".  
7. Save, recompile, and rerun the program to verify your changes.

##### **7.2. HelloWorldImage LibGDX App**

1. Run the LibGDX Project Setup Tool's .jar file using the instructions from Step 2 to generate a new project:
   * Project Name: `helloworldimage`
   * Package: `edu.uma.cgm228.helloworldimage`
   * Main Class: `HelloWorldImage`
   * Select only the **Desktop** platform and leave Languages, Extensions, Template, Third-Party, and the top portion of the Settings page at their defaults.
   * Select the `1.2-hello-world-image-libgdx` folder inside your cloned GitHub repository as the Project Path.
   * You'll see a warning that the project path is not empty; this is expected since the folder contains an image that we'll need - it won't be overwritten.
   * Click **Generate** to generate the project.
2. Open Android Studio.
3. Click Open.
4. Navigate to the folder where you cloned your GitHub repository, select the `1.2-hello-world-image-libgdx` folder, and click **Select Folder** to open it as a project.
5. When prompted, choose **Trust Project**.
6. Wait for Gradle to sync and index the project. Resolve any dependency issues if prompted. Don’t move on until syncing is complete - otherwise, the screen in the next step may look very different.
7. Go to Run > Edit Configurations.  
   * Click the **+** button and select **Application**.
   * In the name field, enter "Desktop".
   * In the `-cp <no module>` drop-down, choose `1.2-hello-world-image-libgdx.lwjgl3.main`.
   * Set the main class to `edu.uma.cgm228.helloworldimage.lwjgl3.Lwjgl3Launcher`.  
   * Set the working directory to `assets` so the game can find its resources.  
   * Click OK to save the configuration.
8. Click the Run button (green triangle) to launch the application and ensure that a window appears displaying the LibGDX logo.
9.  Modify the `core/src/main/java/edu.uma.cgm228.helloworldimage/HelloWorldImage.java` file:  
   * Change the referenced image file from `libgdx.png` to `world.png` or another image that you want to use (e.g., `custom_image.png`).  
   * If using your own image, add your new image file to the assets folder.  
   * Adjust the position of the image by modifying the coordinates in the `batch.draw()` method.  
10. Save, recompile, and rerun the program to verify your changes.

##### **7.3. Explore Interfaces and Abstract Classes**

1. Navigate to the `1.3-interface` folder using the Command Prompt or Terminal (type `cd ../1.3-interface` and press Enter if you're still in the `1.1-hello-world` folder) and run `javac *.java` to compile all classes.
2. Run `java ConcreteUse` to execute the program and see the dialog box.
3. Review the code using your favorite text editor to understand how interfaces are used. Consult resources like [GeeksforGeeks](https://www.geeksforgeeks.org/interfaces-in-java/) for additional insights.  
4. Based on what you have learned, add comments to all three .java files in the `1.3-interface` folder explaining what is happening.  
5. Modify the `bookName()` method in the `JavaBook2.java` file to return the name of our textbook.  
6. Navigate to the `1.4-abstract-class` folder using the Command Prompt or Terminal and again run `javac *.java` to compile all classes.
7. Run `java PayableInterfaceTest` to execute the program and see the output.  
8. Explore how abstract classes are implemented alongside interfaces. Review [GeeksforGeeks](https://www.geeksforgeeks.org/abstract-classes-in-java/) for further reading.  
9. Using the text editor of your choice, create a new class named `HourlyEmployee` that extends `Employee`. You can copy `SalariedEmployee` and then modify it to have class attributes of `weeklyHours` and `hourlyPay` instead of the `weeklySalary`. Create the appropriate getters and setters for the new attributes and modify the constructor and `toString()` method appropriately. The `getPaymentAmount()` method should calculate the payment amount by multiplying the `hourlyPay` by the `weeklyHours`.

##### **7.4. Explore Static Methods and Classes**

1. Navigate to the `1.5-static-class` folder using the Command Prompt or Terminal and run `javac *.java` to compile all classes.
2. Run `java StringUtils` to execute the program and see the output.
3. Review examples of static methods and properties. Consult [CodeGym](https://codegym.cc/groups/posts/what-is-a-static-class-in-java) for more details on static members.  
4. Based on what you have learned, using your text editor of choice, add comments to each of the static methods and attributes in `StringUtils.java` explaining what each is doing and the specific benefit(s) of declaring the method or attribute static.

#### **8\. Review Documentation**

* Spend time reviewing the following documentation to build familiarity:  
  1. [LibGDX API Documentation](https://libgdx.badlogicgames.com/documentation.html).  
  2. [Java Standard API Documentation](https://docs.oracle.com/en/java/javase/).  
  3. [LWJGL API Documentation](https://www.lwjgl.org/).  
* LWJGL (Lightweight Java Game Library) provides access from Java to native APIs such as OpenGL that are used for game development in many programming languages. LWJGL itself was used to create Minecraft Java Edition and is therefore used in developing mods for Minecraft Java Edition. LibGDX is a game development framework that is built on top of LWJGL. As you review the documentation, look for something specific that you want to learn more about. Write a paragraph (150-300 words) explaining what you want to learn more about and why and add it to the bottom of the README.md file in the repository, which can be opened in any text editor. Include the URL for where in the documentation you read about it.

#### **9\. Commit and Push Your Changes**

1. Use GitHub Desktop to commit your changes:  
   * Ensure all modified files and new images are included in your commit.  
   * Write a clear commit message (e.g., "Modified HelloWorld.java to display custom message").  
2. Push your commits to your GitHub repository.

#### **10\. Submit Your Assignment**

1. Navigate to Brightspace and locate the Week 1 folder.  
2. Submit the URL of your GitHub repository under the assignment link.  
3. In the comment box, include a brief description of your modifications (e.g., "Updated HelloWorld.java to display a custom message and modified HelloWorldImage.java to display a custom image at new coordinates").

---

### **Optional Bonus Tasks**

1. Explore the GitHub Student Developer Pack for additional tools.  
2. Experiment with positioning or scaling the displayed image in `HelloWorldImage.java`.

---

### **Grading Criteria**

Your assignment will be graded based on the following:

| Criteria | Weight |
| ----- | ----- |
| Correct setup of Java and Android Studio | 20% |
| Successful program execution | 20% |
| Modifications to Java programs | 30% |
| Proper use of GitHub | 20% |
| Submission and clarity of notes | 10% |

[image1]: <data:image/png;base64,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>