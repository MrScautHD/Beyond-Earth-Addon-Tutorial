![grafik](https://cdn.discordapp.com/attachments/821002652376367114/954447800219877396/logo.png)

# Beyond-Earth-Addon-Tutorial #

![grafik](https://user-images.githubusercontent.com/65916181/157483448-ebbd573e-8a81-40c3-9a62-0c746d4205db.png)

# API #
```groovy
repositories {
    maven { url 'https://jitpack.io' }
}


dependencies {
    implementation 'com.github.MrScautHD:Beyond-Earth:VERSION'
}
````

# How can i add a Renderer (example a new planet) to the Planet Search GUI? #

```java
    @SubscribeEvent
    public static void screenRenderer(ScreenEvent.DrawScreenEvent event) {
        if (event.getScreen() instanceof PlanetSelectionGuiWindow) {
            PlanetSelectionGuiWindow screen = (PlanetSelectionGuiWindow) event.getScreen();

            if (screen.Category >= 0 && screen.Category <= 4) {
                screen.addPlanet(event.getPoseStack(), Events.TEST_PLANET, -90.0F, -90.0F, 10, 10, screen.rotationEarth * 2);
                Events.testCategoryButton.visible = true;
            } else {
                Events.testCategoryButton.visible = false;
            }
        }
    }
```

# How can i add a Button to the GUI? #

```java
    @SubscribeEvent
    public static void screenInit(ScreenEvent.InitScreenEvent event) {
        if (event.getScreen() instanceof PlanetSelectionGuiWindow) {
            PlanetSelectionGuiWindow screen = (PlanetSelectionGuiWindow) event.getScreen();
            PlanetSelectionGui.GuiContainer menu = screen.getMenu();

            Events.testCategoryButton = screen.addImageButtonSetCategory(90, (screen.height / 2) - 24 / 2, 70, 20, PlanetSelectionGuiWindow.defaultButtonTex, 1, menu.getRocket(), 1, screen.tl("test"));
            Events.testCategoryButton.visible = false;
        }
    }
```

# All Code of this class about the Planet Search GUI #

```java
@Mod.EventBusSubscriber(modid = BeyondAddonMod.MODID, value = Dist.CLIENT)
public class Events {
    private static ImageButtonPlacer testCategoryButton;

    //Textures
    public static final ResourceLocation TEST_PLANET = new ResourceLocation(BeyondAddonMod.MODID, "textures/sky/gui/test.png");

    //Renderer
    @SubscribeEvent
    public static void screenRenderer(ScreenEvent.DrawScreenEvent event) {
        if (event.getScreen() instanceof PlanetSelectionGuiWindow) {
            PlanetSelectionGuiWindow screen = (PlanetSelectionGuiWindow) event.getScreen();

            if (screen.Category >= 0 && screen.Category <= 4) {
                screen.addPlanet(event.getPoseStack(), Events.TEST_PLANET, -90.0F, -90.0F, 10, 10, screen.rotationEarth * 2);
                Events.testCategoryButton.visible = true;
            } else {
                Events.testCategoryButton.visible = false;
            }
        }
    }

    //Init
    @SubscribeEvent
    public static void screenInit(ScreenEvent.InitScreenEvent event) {
        if (event.getScreen() instanceof PlanetSelectionGuiWindow) {
            PlanetSelectionGuiWindow screen = (PlanetSelectionGuiWindow) event.getScreen();
            PlanetSelectionGui.GuiContainer menu = screen.getMenu();

            Events.testCategoryButton = screen.addImageButtonSetCategory(90, (screen.height / 2) - 24 / 2, 70, 20, PlanetSelectionGuiWindow.defaultButtonTex, 1, menu.getRocket(), 1, screen.tl("test"));
            Events.testCategoryButton.visible = false;
        }
    }
}
```
