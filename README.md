"A real-time, smart traffic light system prioritizing ambulances, fire trucks, and police vehicles by using live camera feeds and fast AI detection models."


Main Components:

Module | Function
Vehicle Simulation (early stage) | Randomly generate traffic with normal and emergency vehicles.
Priority Queue Logic | Give priority to ambulances > fire engines > police > others dynamically.
Real-Time Camera Input | Capture frames using OpenCV from a real camera or video.
YOLOv8 Object Detection | Detect vehicles like car, bus, truck, ambulance, fire engine, police, bicycle in the frame.
TensorRT Acceleration | Run YOLOv8 extremely fast with NVIDIA TensorRT inference engine.
Dynamic Traffic Light Control | Based on detections, adjust traffic light green time in real-time.
Emergency Handling | Immediately override normal traffic for any detected emergency vehicles.

Workflow:

1. Capture Frame from live camera using OpenCV.
2. Run YOLOv8 TensorRT Detection on the frame.
3. Identify Detected Vehicles (label + bounding box).
4. Feed detections into a priority queue:
5. Emergency vehicles get highest priority.
6. Normal traffic ordered by density/volume.
7. Control Traffic Lights:
8. Emergency vehicles → Full green for 60s.
9. Heavy normal traffic → Dynamic green time.
10. Loop for next frame and keep updating live.

Technology used: 
Technology	Purpose
C++          Main programming language.
OpenCV	     Camera input, frame display, basic image processing.
TensorRT	   Accelerated deep learning model inference (YOLOv8).
YOLOv8	     Object detection (trained to detect vehicles, emergency vehicles).
Priority Queue (C++ STL)	Managing traffic/emergency priorities.
Multithreading (future scope)	For separate camera + processing + controlling in parallel.

Features Achieved:
Real-time emergency vehicle detection
 Intelligent dynamic green light adjustment
 Emergency priority override
 Camera connected to live detection
 Expandable for Smart Cities / IoT setups
