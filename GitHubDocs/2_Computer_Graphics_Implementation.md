# Computer Graphics and OpenGL Implementation

This document outlines how core Computer Graphics and OpenGL concepts are implemented within the project. While the Unity Engine abstracts some of the raw OpenGL C++ calls, the underlying graphics pipeline remains fundamentally based on OpenGL architecture.

## 1. The Graphics Pipeline & OpenGL Usage
The project utilizes the standard 3D rendering pipeline. The geometry of the office, props, and animatronics (Vertices) are processed by vertex shaders for transformation, and fragment shaders are used to calculate the final pixel colors based on textures and lighting.
- **Context:** The engine initializes an OpenGL (or equivalent) context to communicate with the GPU.
- **Shaders:** Standard shaders are used to compute the **Phong Reflection Model** (Ambient, Diffuse, and Specular light).

## 2. 3D Transformations (Model-View-Projection)
All objects in the scene rely on Matrix Transformations:
- **Model Matrix:** Used to position the animatronics. As they move from room to room, translation matrices update their world coordinates, and rotation matrices orient them toward the cameras.
- **View Matrix:** Controlled by the player's mouse movement. The player's head acts as a camera, updating the View Matrix based on pitch and yaw Euler angles.
- **Projection Matrix:** A Perspective Projection matrix is applied to simulate the human eye, providing depth and a realistic Field of View (FOV).

## 3. Dynamic Lighting and Shading
Lighting is a critical mechanic in this project.
- **Point Lights:** Used for the hallway door lights. When the player presses the light button, a Point Light is instantiated/enabled. The fragment shader calculates the distance from the light to the wall vertices to create a falloff effect (attenuation).
- **Ambient Lighting:** Set to a very low value to create a dark, eerie atmosphere.
- **Materials:** Objects use materials that define how they react to light (e.g., metallic surfaces on the animatronics reflect light differently than the wooden desk).

## 4. Texture Mapping & UVs
2D images are wrapped around 3D geometry using UV mapping coordinates.
- **Albedo Maps:** Provide the base color (e.g., the poster on the wall).
- **Normal Maps:** Used to fake high-resolution details on low-polygon models without increasing vertex count. This is heavily used on the walls and animatronic suits to give them a bumpy, realistic texture.

## 5. Off-Screen Rendering (Frame Buffer Objects)
One of the most complex OpenGL features implemented is the Security Camera system.
- **Mechanism:** In raw OpenGL, this is done using an FBO (Frame Buffer Object). A secondary camera is placed in a room. Instead of rendering to the main screen, it renders its output to a 2D Texture in memory.
- **Application:** This texture is then mapped onto the "Tablet" UI quad on the player's screen, allowing the player to view another part of the 3D world in real-time.
