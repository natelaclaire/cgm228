<img src="https://r2cdn.perplexity.ai/pplx-full-logo-primary-dark%402x.png" class="logo" width="120"/>

# Importing a LibGDX Project from BlueJ to Android Studio and Running as a Desktop Game

This guide outlines the steps to migrate your Starfish Collector LibGDX project from BlueJ into Android Studio and configure it to run as a desktop game.

---

## 1. Prepare Your BlueJ Project

- **Export Source Files:** In BlueJ, ensure all your `.java` source files are compiled and saved. Copy the entire project folder to a convenient location on your computer[^1].
- **Export as JAR (Optional):** If you want to keep a backup, you can export your project as a JAR file, but for LibGDX, you’ll primarily need the source files[^1].

---

## 2. Generate a New LibGDX Project

- **Download the LibGDX Project Setup Tool:** Go to the [LibGDX project generation page](https://libgdx.com/wiki/start/project-generation) and download the setup tool (gdx-liftoff)[^2].
- **Run the Setup Tool:** Double-click the downloaded `.jar` file or run it from the command line with `java -jar gdx-liftoff-x.x.x.x.jar`[^2].
- **Configure the Project:**
  - Set the project name (e.g., `StarfishCollector`).
  - Set the package name (e.g., `com.mygdx.starfishcollector`).
  - Choose the platforms: **Desktop** (and optionally Android, HTML, iOS).
  - Click **Generate** to create the project[^2].

---

## 3. Import the Project into Android Studio

- **Open Android Studio.**
- **Import the Project:**
  - Select **File > Open** and navigate to the folder where the LibGDX setup tool generated your project.
  - Select the `build.gradle` file in the root directory and click **OK**[^3].
  - Wait for Gradle to sync and index the project. Resolve any dependency issues if prompted[^3].
- **Project Structure:** The generated project will have submodules like `core` (game logic), `desktop` (desktop launcher), and possibly `android`, `html`, and `ios`[^2].

---

## 4. Move Your Game Code

- **Copy Source Files:**
  - Move your game logic `.java` files from the BlueJ project into the `core/src/main/java/your/package/` directory of the new LibGDX project[^2].
  - Don't move your Launcher class - the project has one.
  - Move any asset files (images, sounds) into the `assets/` directory[^2].
- **Update Package Names:** Ensure your Java files use the correct package declaration matching the new project structure[^2].
- **Change File Paths:** Remove `assets/` from all file paths since the Android and desktop launchers will be configured to treat `assets/` as the working directory.

---

## 5. Configure and Run as a Desktop Game

- **Set Up Run Configuration:**
  - In Android Studio, go to **Run > Edit Configurations**.
  - Click the **+** button and select **Application**.
  - Set the main class to your desktop launcher (e.g., `com.mygdx.starfishcollector.Lwjgl3.Lwjgl3Launcher`).
  - Set the working directory to `core/assets` so the game can find its resources[^4].
  - Name the configuration (e.g., "Desktop")[^5][^6][^4].
- **Run the Game:**
  - Select your new configuration and click the **Run** button (green triangle).
  - The game should launch as a desktop application[^5][^6][^4].
  - Due to some changes in LibGDX, some methods will need to be implemented in BaseScreen and one can be deleted. Press Ctrl-O inside BaseScreen to generate the overrides.

---

## 6. Add Android Support

- **Add On-Screen D-Pad:**
  - Place `dpad-background.png` and `dpad-knob.png` files in `assets`.
  - Add `public static boolean isAndroid = (Gdx.app.getType() == ApplicationType.Android);` property to `StarfishGame` (Alt-Enter automatically adds import statements)
  - Add `private Touchpad touchpad; private float movementSpeed = 200f; // Adjust as needed` properties to `LevelScreen`
  - Add `touchpad = null; if (StarfishGame.isAndroid) { createTouchpad(); }` to `LevelScreen.initialize()` method
  - Add `if (StarfishGame.isAndroid && touchpad != null) { updateMovementFromTouchpad(); }` to `LevelScreen.update()` method - if not on Android, the `Turtle.act()` method will handle keyboard input
  - Add to `LevelScreen`:

```java
private void createTouchpad() {
    // Create touchpad style
    TouchpadStyle touchpadStyle = new TouchpadStyle();

    // Create drawables
    Texture knobTex = new Texture(Gdx.files.internal("dpad-knob.png"));
    Texture backgroundTex = new Texture(Gdx.files.internal("dpad-background.png"));

    touchpadStyle.knob = new TextureRegionDrawable(new TextureRegion(knobTex));
    touchpadStyle.background = new TextureRegionDrawable(new TextureRegion(backgroundTex));

    // Create touchpad
    touchpad = new Touchpad(10, touchpadStyle); // 10px deadzone
    touchpad.setBounds(50, 50, 150, 150); // Position and size

    float dpadSize = Math.min(Gdx.graphics.getWidth()/5f, 200);
    touchpad.setSize(dpadSize, dpadSize);

    // Add to UI stage
    uiStage.addActor(touchpad);
}

private void updateMovementFromTouchpad() {
    float knobX = touchpad.getKnobPercentX();
    float knobY = touchpad.getKnobPercentY();

    if (knobX != 0 || knobY != 0) {
        // Calculate angle in degrees (LibGDX uses 0 degrees = right, 90 = up)
        float angle = (float) Math.toDegrees(Math.atan2(knobY, knobX));
        if (angle < 0) angle += 360;
        turtle.setAcceleration(400); // or whatever value you use
        turtle.accelerateAtAngle(angle);
    } else {
        turtle.setAcceleration(0); // No input, no acceleration
    }
}
```

---

## 7. Troubleshooting Tips

- **Gradle Sync Issues:** If Gradle fails to sync, check your Java SDK version and ensure all dependencies are downloaded[^3].
- **Asset Paths:** If assets are not loading, double-check the working directory in your run configuration[^4].
- **Code Errors:** Refactor any code that uses BlueJ-specific features to standard Java and LibGDX conventions.

---

## Summary Table

| Step | Action | Reference |
| :-- | :-- | :-- |
| Export BlueJ project | Copy source files to a new location | [^1] |
| Generate LibGDX project | Use gdx-liftoff to create a new Gradle-based project | [^2] |
| Import to Android Studio | Open `build.gradle` in Android Studio | [^3] |
| Move code/assets | Place Java files in `core/src/main/java`, assets in `core/assets` | [^2] |
| Configure desktop launcher | Set up run configuration for the desktop module | [^5][^6][^4] |
| Run as desktop game | Use the run configuration to launch the game | [^5][^6][^4] |


---

By following these steps, you can successfully migrate your Starfish Collector project from BlueJ to Android Studio and run it as a desktop game using LibGDX[^5][^2][^3][^4].

<div style="text-align: center">⁂</div>

[^1]: https://www.mta.ca/~rrosebru/oldcourse/171103/tutorial.pdf

[^2]: https://libgdx.com/wiki/start/project-generation

[^3]: https://libgdx.com/dev/from-source/

[^4]: https://www.cs.cornell.edu/courses/cs3152/2021sp/resources/engine/

[^5]: https://www.youtube.com/watch?v=LFs3GiP2Zkc

[^6]: https://www.codeproject.com/Articles/1207754/How-to-Run-Your-Libgdx-Game-on-Your-Desktop

[^7]: https://www.youtube.com/watch?v=UwbfmAtytHc

[^8]: https://gamedev.stackexchange.com/questions/97549/libgdx-android-project-in-intellij

[^9]: https://developer.android.com/studio/intro/migrate

[^10]: https://www.youtube.com/watch?v=XUb97Wv9R6o

[^11]: https://stackoverflow.com/questions/31928693/how-to-export-a-bluej-java-project-into-an-actual-exe-type-program-not-jar

[^12]: https://www.vbforums.com/showthread.php?882759-RESOLVED-How-to-export-my-project-on-Bluej-to-executable-(-exe)

[^13]: https://www.youtube.com/watch?v=l5VnCRwt1d0

[^14]: https://2021.desosa.nl/projects/libgdx/posts/architecture/

[^15]: https://libgdx.com/wiki/start/import-and-running

[^16]: https://stackoverflow.com/questions/42156926/how-to-add-libgdx-to-an-existing-android-studio-project

[^17]: https://www.reddit.com/r/libgdx/comments/ezquo5/importing_initial_libgdx_build_to_android_studio/

[^18]: https://stackoverflow.com/questions/23945407/when-i-convert-a-java-project-to-a-jar-with-bluej-the-project-doesnt-work-as

[^19]: https://forums.codeguru.com/showthread.php?486086-How-do-I-export-a-program-from-BlueJ

[^20]: https://courses.cs.umbc.edu/331/resources/java101/jar.html

