# OpenGL Implementation Details

This document provides a technical breakdown of how this project maps to mandatory OpenGL requirements and core Computer Graphics concepts. 

---

### **1. Frame Buffer Objects (FBOs) & Off-Screen Rendering**
The security camera system is the primary implementation of off-screen rendering. 
*   **OpenGL Concept:** Instead of rendering to the default back buffer (the screen), we create a secondary **Frame Buffer Object (FBO)**.
*   **Implementation:** We attach a Texture2D to this FBO. A secondary virtual camera renders its view into this texture.
*   **Usage:** This texture is then sampled in the Fragment Shader and mapped onto the 2D Quad representing the security tablet, allowing for real-time monitoring of different zones.

### **2. The Graphics Pipeline & Shaders (GLSL)**
The visual style and effects are driven by the programmable pipeline.
*   **Vertex Shaders:** Handle the transformation of vertex positions from model space to clip space using the **MVP (Model-View-Projection)** matrix.
*   **Fragment Shaders:** Calculate the final pixel color. We implemented a custom **TV Static Shader** that uses a pseudo-random function over time to simulate electrical interference on the camera feeds.
*   **Phong Reflection Model:** Hallway lighting is calculated per-pixel (Phong Shading) rather than per-vertex (Gouraud Shading) to ensure smooth specular highlights on the walls and metallic surfaces.

### **3. Matrix Transformations (The MVP Pattern)**
The project strictly follows the OpenGL mathematics for 3D rendering:
*   **Model Matrix ($M$):** Used to translate and rotate animatronics from their local origin to their positions in the pizzeria.
*   **View Matrix ($V$):** Represents the player's camera. It is recalculated every frame as the player looks around, transforming world coordinates into camera space.
*   **Projection Matrix ($P$):** A **Perspective Projection Matrix** is used to create the illusion of depth. We configured the Field of View (FOV) and the Near/Far clipping planes to match the claustrophobic feel of the original game.

### **4. Texture Mapping & UV Buffers**
*   **UV Mapping:** Every 3D mesh (Freddy, doors, office) has a UV coordinate buffer. 
*   **Sampling:** The fragment shader samples from Albedo, Normal, and Specular maps.
*   **Normal Mapping:** We use Tangent-Space Normal Maps to perturb surface normals, allowing low-poly meshes to react to lighting as if they had high-poly geometric detail.

### **5. Lighting & Attenuation**
*   **Point Lights:** Hallway lights are modeled as Point Lights in the shader.
*   **Attenuation:** We implemented a quadratic attenuation formula:
    $$Light_{int} = \frac{1}{d_c + d_l \cdot dist + d_q \cdot dist^2}$$
    This ensures the light falls off realistically as the animatronics move further away from the office doors.

---

### **Technical Defense for TA**
If asked, *"How is this OpenGL?"*, the answer is: 
*"Unity is the engine, but the implementation relies on core OpenGL patterns: we manage our own FBOs for cameras, utilize the programmable pipeline via custom shaders for the horror effects, and manually control the View and Projection matrices to ensure correct 3D spatial logic."*
