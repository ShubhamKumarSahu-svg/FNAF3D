# Gameplay & Survival Guide

This guide covers the core mechanics and controls of the FNAF 3D project.

### **The Objective**
You are a night security guard at a pizzeria. Your goal is simple: **Survive until 6:00 AM** without letting the animatronics enter your office.

---

### **Controls & Interface**
*   **Mouse Look:** Move your mouse to look left and right. The camera is clamped to ensure you can see both security doors.
*   **Door Buttons (Red/White):** Click the physical buttons on the wall next to the doors to open or close them.
*   **Light Buttons:** Click the buttons below the door controls to toggle the hallway lights. Use these to check if an animatronic is standing right outside your door.
*   **Camera Tablet:** Move your cursor to the bottom of the screen to bring up the security tablet.
    *   **Camera Switching:** Click the numbered boxes on the map to switch between real-time camera feeds.

---

### **The Power Management System**
This is a critical part of the game's logic. You have a limited battery (100%).
*   **Usage Levels:** The more systems you use, the faster your battery drains. 
    *   **Level 1:** Passive drain (everything off).
    *   **Level 2-4:** Incremental drain for every door closed, light turned on, or camera active.
*   **The Blackout:** If your power hits **0%**, all doors will open, the cameras will go dead, and you will be left in total darkness.

---

### **The Animatronics (AI Logic)**
*   **Bonnie (Left Hallway):** He is aggressive and moves frequently.
*   **Chica (Right Hallway):** She tends to stay at the door longer once she arrives.
*   **Foxy (Pirate Cove - Cam 1C):** If you don't check him frequently, he will sprint down the West Hallway. If he is missing from the camera, **close your left door immediately**.
*   **Freddy (The Shadows):** He is the most stealthy and usually moves later in the week or when the power is out.

---

### **Technical Highlights for Evaluation**
1.  **Render-to-Texture System:** The security tablet uses real-time off-screen rendering (FBOs).
2.  **View Matrix Logic:** Smooth mouse-look implementation using Euler angle clamps.
3.  **Dynamic Lighting:** Real-time point light attenuation for the hallway indicators.
