# Understanding & Q/A Preparation

This document contains expected questions from the TA during the evaluation and the logic/answers behind them.

---

### **Q1: Where exactly is OpenGL used in this project? I see you are using an engine.**
**Answer:** While we used a game engine to streamline development, the engine is simply an abstraction layer over OpenGL (or DirectX/Vulkan depending on the build). Every frame rendered on the screen requires OpenGL calls. Specifically, we leveraged OpenGL concepts such as **Frame Buffer Objects (FBOs)** for our security cameras (rendering to a texture), **Matrix Transformations** (MVP matrices) to move the animatronics, and the **Phong Reflection Model** in our fragment shaders for the flashlight and hallway lights.

### **Q2: Explain how the animatronics move from room to room in the context of Computer Graphics.**
**Answer:** The animatronics are defined by a set of vertices in local space. To move them, we apply an Affine Transformation to their **Model Matrix**. When an animatronic decides to move to a new room, we update its translation vector $(T_x, T_y, T_z)$ and rotation vector $(R_x, R_y, R_z)$. The graphics pipeline multiplies the vertices by this new Model Matrix, effectively updating their position in world space.

### **Q3: How does your security camera system work?**
**Answer:** It uses off-screen rendering. Normally, a camera renders to the default frame buffer (the screen). For the security cameras, we instruct a secondary virtual camera to render its view into an allocated texture memory block (an FBO in OpenGL terms). We then take this generated 2D texture and apply it as a material onto a 2D Quad in our User Interface. 

### **Q4: How did you implement lighting, and what type of shading is used?**
**Answer:** We are using dynamic lighting based on the Phong or Blinn-Phong shading model. For the hallway lights, we use **Point Lights**. The fragment shader calculates the color of the wall pixels based on the distance from the light source (attenuation), the angle of the light hitting the surface (diffuse), and the viewer's angle (specular reflection). 

### **Q5: What is a Normal Map and how did you use it?**
**Answer:** A normal map is an RGB texture where the colors represent X, Y, and Z coordinates of surface normals. Instead of adding thousands of vertices to make a wall look bumpy or a suit look worn, the fragment shader uses the normal map to alter the way light bounces off a flat polygon, faking high-resolution depth and detail.

### **Q6: How is the player's view controlled?**
**Answer:** The player's view is controlled by updating the **View Matrix**. As the user moves the mouse, we capture the delta movement and calculate new pitch (X-axis) and yaw (Y-axis) Euler angles. We apply these rotations to the camera's transform, which recalculates the View Matrix, changing what part of the world is projected onto the screen.
