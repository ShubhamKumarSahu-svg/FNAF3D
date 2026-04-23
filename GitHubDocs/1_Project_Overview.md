# Project Overview and Originality

## Project Title
**FNAF 3D: A Real-Time Survival Horror Experience**

## Objective
The objective of this project is to implement core computer graphics concepts to create a real-time 3D survival horror game. By utilizing an underlying graphics API (OpenGL), the project demonstrates the practical application of 3D transformations, dynamic lighting, texture mapping, and off-screen rendering.

## Originality & Innovation
While the original *Five Nights at Freddy's* utilized pre-rendered 2D images to simulate a 3D environment, this project innovates by rendering the entire environment in **real-time 3D**. This transition required solving several computer graphics challenges:
- **Dynamic Lighting:** Instead of static baked lighting, the player can dynamically toggle hallway lights, requiring real-time calculation of diffuse and specular lighting components.
- **Spatial Audio & 3D Positioning:** The animatronics exist in true 3D space, meaning their presence is governed by standard 3D affine transformations (translation and rotation) rather than simple 2D frame swapping.

## Project Complexity
The project achieves a high level of complexity suitable for a Computer Graphics Lab by integrating:
1. **Multiple Camera Systems:** Implementing both a primary player camera (Perspective Projection) and secondary security cameras.
2. **Render-to-Texture (FBOs):** Utilizing Frame Buffer Objects to render camera feeds onto 2D UI elements dynamically.
3. **Resource Management:** Balancing the rendering load (dynamic lights vs. ambient lighting) to simulate the "power drain" mechanic of the game.
4. **State Machine Transformations:** Managing the translation matrices of multiple complex 3D meshes (animatronics) simultaneously across the scene.
