# shared-dctl

A collection of my personal DCTLs that I’m making available to the community.  
Right now, these DCTLs are shared in **encrypted form**, meaning you can use them but not access the source code.  

I’m considering making parts of this library fully open-source in the future.  
If that happens, the repo will be updated with source code, documentation, and a clear licensing model.



## Disclaimer
These tools are provided as-is, without warranty or guarantee of fitness for any particular purpose.  
Use at your own risk.



## License
Currently **no license is granted** for modification or redistribution of the encrypted DCTLs.  
You are free to download and use them in your grading projects.  
An open-source license (likely MIT or Apache 2.0) may be added in the future if the source is released.



## Included DCTLs

### **OSD Contrast**
OSD Contrast uses a cubic spline curve to shape contrast around a pivot point.
When **AutoSlope** is enabled, the tool automatically adjusts the curve’s transitions to keep highlight and shadow slopes balanced.
A **Preserve Saturation** slider lets you control how much color saturation is affected by contrast adjustments.

### **OSD Halation**
A creative, film-like halation effect designed to add a warm glow around highlights.  
It uses a soft Gaussian blur applied to the red and green channels to create a natural orange halo while keeping the blue channel clean.  

The look can be adjusted with **intensity**, **tint**, **threshold**, and **rolloff** controls, while a **matte preview** mode helps visualize the affected areas.  

While not intended as a film-accurate emulation, this DCTL offers a quick and flexible way to introduce a halation-style effect that reacts naturally to light.  
Because it currently relies on a generic **Rec.709-style luma mix**, results may vary slightly across different color gamuts.  
A future version may include gamut-aware processing to ensure consistent behavior between color spaces.  

Two quality modes are available: **Performance** for speed, and **Precision** for smoother results.  
The effect itself can become GPU-intensive at higher intensity values, even in Performance mode.

### **OSD Transform**
The centerpiece of this project.  
It works similarly to the Color Space Transform OFX in Resolve, but expands on it with my custom color space: the **OSDwcs** (OSD Working Color Space), currently in development.  

OSDwcs combines:  

- **OSD Log8P413**  
  A custom transfer function where **8 printer light points (offset)** equal **1 stop of light**.  
  Middle gray (0.18 in linear) is mapped to **0.413**.  

- **OSD Wide Gamut**  
  A custom wide gamut color space (development version 0.08).  
  Designed to encompass some of the main industry gamuts: **AWG3, AWG4, S-Gamut3.cine, ACES AP1, Rec.709, Rec.2020, and P3**.  

A white paper with full specifications will eventually be released.

Currently, the available Display Render Transforms (DRT) support **Rec.709** and **P3-D65** displays, with gamma options of **2.2, 2.4, and 2.6**. Work is in progress on implementing the **SMPTE ST2084 PQ** curve for HDR.  

**Note:**  When using OSD Transform with a DRT as output (output to a display space), it is strongly recommended to set **Clamp** to **Output**.  
This prevents negative pixel values that can appear in extreme luminance or color conditions.
A future **Auto Clamp** mode is planned to handle these cases automatically.

Beyond color space management, OSD Transform also includes a scene refered **false color overlay**, mapped in stops of light:  
- Purple: −6 stops
- Blue: −4 stops  
- Green: 0 stop (middle gray)  
- Pink: +1 stop  
- Yellow: 2 stops under Red  
- Red: user-defined “highlight ceiling” range

### **Coming Soon – OSD Balance**  
A lightweight DCTL for quick image balancing.  
It includes an **Exposure** control, a **Contrast** slider (with optional saturation preservation), and straightforward **Temperature** and **Tint** adjustments based on linear gain operations.
