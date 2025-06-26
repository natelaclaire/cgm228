# Final Class

## Gradle Sync

Ctrl-Shift-O or button next to Search Everywhere at top of screen
May need to go to Gradle pane and click link to turn on experimental settings, always build all gradle tasks during sync

## Controllers

chapter 13 discusses controllers and touchpads

1. BaseScreen
   1. Implements ControllerListener
   2. Override ControllerListener methods
   3. Add property: `protected Controller controller;`
   4. In show() method: `Controllers.addListener(this); if (Controllers.getCurrent() != null) { controller = Controllers.getCurrent(); }`
   5. In hide() method: `Controllers.removeListener(this); controller = null;`
   6. In connected() method: `this.controller = controller;`
   7. In disconnected() method: `if (this.controller == controller) this.controller = null;`
2. LevelScreen
   1. In update() method: `if (controller != null) { updateMovementFromController(); }`
   2. Add code for updateMovementFromController() below
   3. Optionally, implement buttonDown() or buttonUp(), or axisMoved()

```java
private void updateMovementFromController() {
     float axisX = controller.getAxis(0);
     float axisY = controller.getAxis(1);

     // axisY is reversed on the controller
     axisY = -axisY;

     if (axisX > 0.5f || axisX < -0.5f || axisY > 0.5f || axisY < -0.5f) {
         // Calculate angle in degrees (LibGDX uses 0 degrees = right, 90 = up)
         float angle = (float) Math.toDegrees(Math.atan2(axisY, axisX));
         if (angle < 0) angle += 360;
         turtle.setAcceleration(400); // or whatever value you use
         turtle.accelerateAtAngle(angle);
     } else {
         turtle.setAcceleration(0); // No input, no acceleration
     }
}

@Override
public boolean buttonDown(Controller controller, int buttonCode) {
     // treat the B button as restart
     if (buttonCode == controller.getMapping().buttonB) {
         instrumental.dispose();
         oceanSurf.dispose();

         StarfishGame.setActiveScreen(new LevelScreen());
         return true;
     }

     return false;
}
```

3. MenuScreen
   1. Could implement buttonUp() to enable using controller to start game
  
```java
@Override
public boolean buttonDown(Controller controller, int buttonCode) {
     // treat the B button as restart
     if (buttonCode == controller.getMapping().buttonA) {
         StarfishGame.setActiveScreen( new LevelScreen() );
         return true;
     } else if (buttonCode == controller.getMapping().buttonB) {
         Gdx.app.exit();
         return true;
     }

     return false;
}
```

## Android Scaling

Discuss [Viewports](https://libgdx.com/wiki/graphics/viewports)

In BaseScreen class, replace mainStage and uiStage instantiation lines with:

```java
mainStage = new Stage(new FillViewport(800, 600));
uiStage = new Stage(new ExtendViewport(800, 600));
```

Add code for BaseScreen.resize():

```java
mainStage.getViewport().update(width, height, true);
uiStage.getViewport().update(width, height, true);
```

In BaseScreen.render(), replace:

```java
mainStage.getViewport().apply();
mainStage.draw();
uiStage.getViewport().apply();
uiStage.draw();
```

## HTML

It turns out that we can't use FreeTypeFontGenerator with an HTML project because it uses some native code that can't be transpiled to JavaScript. If you want to build an HTML game with LibGDX, you should use Hiero to generate a bitmap font outside of your application and load it in your application using the BitmapFont class as we discussed a few weeks ago.

If your game supported HTML, we could:

1. In terminal, run `.\gradlew html:superDev` to test
2. In terminal, run `.\gradlew html:dist` to build the HTML and JavaScript files that can be deployed to a Web server

See <https://www.youtube.com/watch?v=I_85usDvJvQ&ab_channel=Raeleus> and <https://libgdx.com/wiki/deployment/deploying-your-application#deploy-web>


## Deploying Your Application

Windows:
./gradlew lwjgl3:dist
lwjgl3/build/libs/

Or Gradle task: lwjgl3/construo/packageWinX64
lwjgl3/build/construo/dist for zip or lwjgl3/build/construo/winX64/roast for individual files

Construo tasks can be used for build for various platforms from any platform - nice!

<https://libgdx.com/wiki/deployment/deploying-your-application>

### Android Packaging

.\gradlew android:assembleRelease

android/build/outputs/apk/release

<https://libgdx.com/wiki/deployment/deploying-your-application#deploy-to-android>

### Android Distribution

<https://www.youtube.com/watch?v=L9sU_aGeQEY&ab_channel=iRekhaTechSolutions>

## Physical Phone?
