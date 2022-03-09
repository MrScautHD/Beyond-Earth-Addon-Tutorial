![grafik](https://user-images.githubusercontent.com/65916181/157483349-116daea1-f64c-4c97-8b70-1cbf009d3860.png)

# Beyond-Earth-Addon-Tutorial #

![grafik](https://user-images.githubusercontent.com/65916181/157483448-ebbd573e-8a81-40c3-9a62-0c746d4205db.png)

# How can i add a Renderer (example a new planet) to the Planet Search GUI #

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
