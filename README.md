# [Spacemoji](https://j-ncel.github.io/Spacemoji/)

A single-file HTML5 Canvas animation that simulates a journey through emoji-filled space. The experience features 3D perspective projection and a smooth warp transition.

[**View Live Demo**](https://j-ncel.github.io/Spacemoji/)

![snapshot of spacemoju](snapshot.gif)

## Interaction

- **Click/Tap & Hold:** Warp through space.
- **Release:** Disengages warp.

## Configuration Guide

The behavior is dictated by `this.config`. Here is a breakdown of the primary parameters:

| Parameter                   | Default | Description                                                                                                  |
| :-------------------------- | :------ | :----------------------------------------------------------------------------------------------------------- |
| **totalParticles**          | 700     | The total number of emojis active in the simulation.                                                         |
| **farZLimit**               | 3000    | The spawn distance, how far away emojis start in the Z-axis.                                                 |
| **focalLength**             | 1000    | The simulated lens width. Higher values create a "zoom" effect; lower values create "wide-angle" distortion. |
| **baseSpeed**               | 3       | The constant velocity of travel without interaction.                                                         |
| **warpSpeed**               | 100     | The maximum speed achieved during a hold interaction.                                                        |
| **accelerationRate**        | 0.05    | How quickly the engine transitions between base and warp speeds.                                             |
| **motionTrailOpacity**      | 0.3     | Controls the trail effect. Lower values create longer trails.                                                |
| **spawnSpreadRange**        | 5000    | The range of emoji spawn. Lower values, more compress.                                                       |
| **rotationSpeedMultiplier** | 0.0005  | The base rate at which emojis spin as they travel.                                                           |

## 3D Projection Math

It maps 3D world coordinates $(X, Y, Z)$ to a 2D viewport using a perspective projection model. This creates the illusion of depth and movement toward the viewer.

The screen coordinates $(screenX, screenY)$ are calculated as follows:

$$screenX = \frac{worldX \cdot focalLength}{worldZ} + centerX$$
$$screenY = \frac{worldY \cdot focalLength}{worldZ} + centerY$$

As $worldZ$ decreases (the particle moves closer), the perspective factor increases, making the emoji appear larger and move faster across the screen.
