<div class="dm-card">

The Python script implements a real-time computer vision system to track people in a video feed
and analyze their horizontal distribution. It then sends this distribution data as Open Sound
Control (OSC) messages to Max for Live for sound control.

1. Overall Purpose  
The script takes video input from a specified camera, uses background subtraction to isolate
moving objects (assumed to be people), tracks these objects over time, and calculates the
following metrics for the detected crowd:  
1. Count: The number of stable, currently tracked people.  
2. Average X: The horizontal center-of-mass of the crowd, normalized from 0.0 (far left) to
1.0 (far right).  
3. Concentration: A measure of how tightly clustered the people are horizontally, ranging
from 0.0 (maximally spread) to 1.0 (maximally clustered).

2. Dependencies and Setup  
- cv2 (OpenCV): video capture and computer vision processing.  
- pythonosc.udp_client: send OSC messages over the network.  
- numpy: numerical operations.

3. Main Tracking and OSC Logic  

Initialization  
1. OSC Client: udp_Client.SimpleUDPClient is initialized to send messages to the specified
IP and port  
2. Video Capture: cv2.VideoCapture  
3. Background Subtraction: cv2.createBackgroundSubtractorMOG2 learns the stationary
background and outputs a mask showing only moving foreground objects.  
4. Tracking State: tracks is used to store the state of currently tracked people (position, size,
last time seen, number of hits).

Frame Processing (Computer Vision)  
1. Noise Reduction: A Gaussian blur is applied to the frame before background
subtraction.  
2. Morphological Operations: The foreground mask is cleaned using Opening (removes
small noise) and Closing (fills small holes).  
3. Dilation: The mask is slightly dilated to merge adjacent, broken-up blobs into single
detections.  
4. Thresholding: A final binary threshold is applied to ensure the mask consists only of black
and white pixels  
5. Contour Finding: cv2.findContours finds distinct shapes in the mask. Those smaller than
args.min_area are discarded.

Tracking  
The script implements a simple tracking algorithm based on the horizontal center of each
detection.  
1. Matching: Each new detection is compared to existing active tracks. It finds the nearest
track based on the x-coordinate distance. A match is confirmed if the distance is less than
1/6 of the frame width (w / match_dist_fraction).  
2. Updating: If a match is found, the track’s position is updated, and its last_seen time and
hits count are incremented.  
3. New Tracks: If a detection cannot be matched to a nearby existing track, a new track ID is
assigned.  
4. Aging Out: Tracks that have not been seen (detected) for longer than args.hold seconds
are removed from the system.

OSC Message Sending  
OSC messages are sent at the rate defined by args.fps.  
1. Active Tracks Filtering: Only tracks that have been seen recently (last_seen within
args.hold) AND have been stable (hits >= args.persist) are considered active tracks for
distribution analysis.  
2. Calculations:  
- Normalized X: The horizontal center (cx) of each active track is normalized to the frame
width (w) to get a value between 0.0 and 1.0.  
- Average X (μx): Calculated as the mean of all normalized X-positions.  
- Concentration: Calculated from the standard deviation (σx) of the normalized X-positions:  

Concentration = max(0.0, 1.0 − min(σx / 0.5, 1.0))

- A low σx (people clustered) results in a high concentration score (close to 1.0).  
- A high σx (people spread out) results in a low concentration score (close to 0.0).  

3. Sending Messages: The following three OSC messages are sent:  
- /people/count: The number of active people  
- /people/avgx: The average normalized X-position (center of crowd).  
- /people/concentration: The calculated concentration value.

Visualization  
If the —show argument is used, a debug window is displayed showing:  
- Green rectangles around the current frame’s detections.  
- Circles marking the center of each track.  
- Blue circles indicate stable tracks (hits >= persist).  
- Red circles indicate new/unstable tracks.  
- The opacity of the track circle fades as its last_seen time approaches the args.hold limit.

Cleanup  
When the script exits (by pressing ‘q' in the display window), the camera is released, and all
OpenCV windows are closed.

</div>