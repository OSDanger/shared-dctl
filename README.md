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

### **OSDContrast**
A lightweight tool focused on contrast manipulation.  
Simple, direct, designed for clean adjustments without unnecessary complexity.

### **OSDHalation**
A minimalistic halation formula I’ve been experimenting with.  
It aims to add a subtle glow/red channel bloom effect inspired by film behavior.

### **OSDTransform**
The centerpiece of this project.  
It works similarly to the Color Space Transform OFX in Resolve, but expands on it with my custom color science: the **OSDwcs** (OSD Working Color Space), currently in development.  

OSDwcs combines:
- **OSD Log8P413** : a custom transfer function  
- **OSD Wide Gamut** : a custom wide gamut color space (development version 0.08)  

A white paper with full specifications will eventually be released.

Beyond color space management, OSDTransform also includes a **false color overlay**, mapped in stops of light:  
- Purple: −6 stops  
- Blue: −4 stops  
- Green: 0 stop (middle gray)  
- Pink: +1 stop  
- Yellow: 2 stops under Red  
- Red: user-defined “highlight ceiling” range  