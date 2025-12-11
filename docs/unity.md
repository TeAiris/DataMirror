<div class="dm-card" markdown>

# Unity Overview

Unity served as the primary interface for programming interaction, spatial audio control, and responsive visuals throughout the project.  
It functioned as the central hub bridging visual effects, OSC communication, and interactive 3D elements.

![Unity Overview Placeholder](./media/dm3.gif)

</div>



<div class="dm-card" markdown>

# Matrix Visual Effects & Shaders

The Matrix VFX library and shader tools were used to stylize the virtual space with falling green characters.  
These shaders were extended to support:

- HSV color manipulation  
- Adjustable speed and density  
- Scalable flow patterns  
- Mapping the Matrix effect directly onto a 3D avatar mesh  

This pipeline allowed the Matrix aesthetic to function as both a background effect and an integrated visual element on characters and world geometry.

![Matrix Shaders Placeholder](./media/shaders.mov.gif)

</div>



<div class="dm-card" markdown>

# Avatar Integration & Animation

Subtle idle animations were added to the avatar to create natural, life-like movement.  
When combined with shader-driven Matrix text mapped to the avatar, the visual system became more expressive and immersive.

![Avatar Placeholder](./media/ava.gif)

</div>



<div class="dm-card" markdown>

# Virtual Reconstruction of Physical Space

To align virtual and real-world systems, the installation environment at **Underground Atlanta** was modeled in detail.

- DWG files from **Global Truss** were used for dimensional accuracy  
- The spatial speaker array was modeled and positioned to match the physical setup  
- The completed structure was exported as FBX and imported into Unity  

Once inside Unity, Matrix character effects were applied to the walls, and a grid-texture contrast layer was added to create motion depth.  
Additional camera distortion effects enhanced immersion and drew participants deeper into the environment.

![Virtual Space Placeholder](./media/truss1.png)

</div>



<div class="dm-card" markdown>

# Spatial Audio Interaction System

## Spatial Animation Player

The **Spatial Animation Player** script is the core interaction system.  
It enables intuitive visualization and control of spatial audio.

Key components include:

- A defined 3D interactive zone  
- Glowing orb markers for sound origins  
- Mirrored spatial layouts (inspired by Dolby Atmos panning tools)  
- OSC routing via extOSC to the **IEM Stereo Encoder** inside Reaper  

Unity’s world-space coordinates are continuously converted into:

- **Azimuth**  
- **Elevation**  
- **Roll**  

These values drive Reaper’s spatial panner for each stem track.

With Unity and Reaper connected at runtime, the **Nulea M512 trackball mouse** provides fluid, intuitive control of sound object positioning.

![Spatial Animation Player Placeholder](./media/spa.png)

</div>



<div class="dm-card" markdown>

# SpatialMouse Extensions

The **SpatialMouse** script expands interactivity and visualization through real-time mouse-based effects:

- Light-based highlights projected onto virtual speakers  
- Visual cues that help users understand sound direction  
- A cycling system for toggling stem-mirroring modes via the top-left mouse button  

These additions create a more expressive and approachable spatial mixing interface, blending sound control with visual feedback.

![SpatialMouse Placeholder](./media/sp.png)

</div>