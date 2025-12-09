<div class="dm-card" markdown>

# Tech Details  

### Hardware  
- **[MacBook Pro 14" (Apple Silicon)](https://www.apple.com/macbook-pro-14-and-16/)**, main control computer running Ableton Live 12, Unity + OSC routing to Reaper  
- **[Midas M32](https://www.midasconsoles.com/product.html?modelCode=0603-AEO)**, used as both the audio interface and multichannel mixer  
- **[Neumann KH 120](https://www.neumann.com/en-us/products/monitors/kh-120-ii)**, primary spatial speakers (head-level arc and front overhead)  
- **[QSC K10.2](https://www.qscaudio.com/solutions-products/loudspeakers/portable/powered/portable-pa/k2-series/k102/)**, floor-level reinforcement  
- **[Alto Professional TS18C Subwoofer](https://www.altoprofessional.com/products/ts18s)**, low-end reinforcement  
- **Projector**, front-wall visuals *(model varies)*  
- **[Roland V-1HD Video Mixer](https://proav.roland.com/global/products/v-1hd/)**, blends camera feed and OpenCV output with Unity projections  
- **[Intel RealSense D455f Depth Camera](https://www.intel.com/content/www/us/en/products/sku/233193/intel-realsense-depth-camera-d455f/specifications.html)**, crowd tracking and centroid estimation  
- **[Nulea M512 Wireless Trackball Mouse](https://nulea.com/products/nulea-m512-wireless-trackball-mouse)**, spatial-panning controller  


![Hardware Collage Placeholder](./media/Hardware.png)

</div>

<div class="dm-card" markdown>

### Software  
- **[Unity](https://unity.com/)**, visual environment, shader system, OSC output  
- **[Ableton Live](https://www.ableton.com/live/)**, 8-scene stem engine  
- **[Reaper](https://www.reaper.fm/)**, IEM spatial audio processing  

#### Software Icons  
![Software Icons Placeholder](./media/Software.png)

</div>

<div class="dm-card" markdown>

### Libraries / Plugins  
- **[IEM Ambisonics Suite](https://plugins.iem.at/)** (Object-Based Panner, Scene Rotator, In-Ear, etc.)  
- **[#extOSC – Open Sound Control](https://github.com/Iam1337/extOSC)**, system-wide OSC routing  
- **[OpenCV](https://opencv.org/)**, depth tracking and centroid extraction  

#### Libraries Graphic  
![Libraries Graphic Placeholder](./media/Libraries.png)   


#### Real-Time Matrix VFX  
**[MatrixVFX](https://github.com/IRCSS/MatrixVFX?tab=readme-ov-file)**

![Matrix VFX Placeholder](./media/matrixg.gif)  


</div>

<div class="dm-card" markdown>

## System Diagram / Data Flow

![System Diagram Placeholder](./media/Hardware.png) 


## Interaction Design  

### User Actions  
- Move through physical space  
- Use the Nulea trackball to spatialize stems  
- Toggle stem groups and mirror modes  
- Observe visuals reacting to movement and input  

### System Responses  
- Real-time spatial changes  
- Matrix shader effects and avatar feedback  
- Tempo changes based on group clustering  
- Progression through eight stem sets  

</div>

<div class="dm-card" markdown>

## Implementation Details  

### Unity  
- Matrix shader environment  
- 3D speaker-array visualization  
- Data-avatar representation  
- See **Unity** tab. 

### Reaper  
- Four routed tracks: **Drums, Bass, Harmony, Melody**  
- IEM suite for spatialization  
- OSC parameter mapping  

### Ableton  
- Eight musical scenes  
- Outputs four stems directly to Reaper  
- Receives tempo modulation from Unity  

### BPDistributions.py  
- see **BPDistrubtion** tab

</div>

<div class="dm-card" markdown>

## Requirements & Setup  

### Software Needed  
- Unity  
- Reaper + IEM plugins  
- Ableton Live  
- Python 3  

### Hardware Connections  
- M32 → all speakers  
- Projector → HDMI  
- RealSense camera → USB-C  
- Trackball → USB Dongle or Bluetooth

### Running the System  
1. Launch Reaper  
2. Load Ableton stem sets  
3. Open Unity scene  
4. Confirm OSC routing  
5. Begin interaction  


</div>