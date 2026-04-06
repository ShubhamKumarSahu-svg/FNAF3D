# Presentation Outline (PPT Structure)

This outline is designed to hit all the key points in the 10-15 minute evaluation timeframe, matching the required marking rubric.

### Slide 1: Title Slide
- **Project Title:** FNAF 3D - A Real-Time Graphics Experience
- **Team Members:** Shubham Kumar Sahu
- **Course:** Computer Graphics Lab

### Slide 2: Project Objective
- Briefly explain the goal: To recreate a popular survival horror game using real-time 3D rendering.
- Highlight the shift from 2D pre-rendered graphics to true 3D spatial environments.

### Slide 3: Originality & Complexity
- **Originality:** Converting a static 2D game into a fully explorable/rendered 3D space with dynamic lighting.
- **Complexity:** Managing multiple light sources, complex state machines for AI, and real-time Render-to-Texture (FBO) systems.

### Slide 4: Computer Graphics Implementations (The Core)
- Detail the 4 main pillars used:
  1. **3D Transformations:** (Model, View, Projection matrices)
  2. **Lighting Models:** (Phong shading, dynamic point light attenuation)
  3. **Texture Mapping:** (UVs, Albedo, and Normal Maps)
  4. **Off-Screen Rendering:** (FBOs for the camera system)

### Slide 5: The Graphics Pipeline in Action
- Show a diagram or screenshot of the game.
- Explain how vertices (animatronics/office) go through the Vertex Shader, and how textures/lights are applied in the Fragment Shader.

### Slide 6: Deep Dive - Security Cameras
- Explain the Render-to-Texture concept.
- "We use Frame Buffer Objects (FBOs) to capture a secondary camera's view and map it as a texture onto the UI tablet."

### Slide 7: Project Development
- **Shubham Kumar Sahu:** Graphics pipeline, Dynamic Lighting, Render-to-Texture system, 3D Transformations, View Matrix logic, Texture mapping, FOV tuning, and Material specularity.

### Slide 8: Live Demonstration (Ready-to-run Code)
- *Switch to the running application.*
- Demonstrate the View Matrix (looking around).
- Demonstrate dynamic lighting (turning hallway lights on/off).
- Demonstrate the FBO system (opening the camera tablet).

### Slide 9: Q&A
- "Thank you! We are ready for your questions."
