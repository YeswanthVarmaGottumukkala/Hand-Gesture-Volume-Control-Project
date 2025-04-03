# Hand-Gesture-Volume-Control-Project
## Overview  
This project uses OpenCV, MediaPipe, and Pycaw to control system volume through hand gestures. The program detects hand movements via the webcam and adjusts the volume based on the distance between the thumb and index finger.  

## Libraries Used  
- `cv2` – OpenCV for image processing  
- `time` – To calculate FPS  
- `numpy` – For mathematical operations  
- `HandTrackingModule` – Custom module for hand tracking  
- `math` – To calculate distance between fingers  
- `pycaw` – To control system audio  
- This distance acts as the **input** for volume control.

## How It Works  

### 1️⃣ Initializing Webcam  
- The script starts by **capturing video** from the webcam using OpenCV.  
- The resolution is set for better accuracy and visualization.  

### 2️⃣ Detecting Hands  
- The **HandTrackingModule** (built using MediaPipe) detects hand landmarks in real time.  
- Each hand landmark is assigned a unique ID, allowing precise tracking of fingers.  

### 3️⃣ Identifying Thumb & Index Finger  
- The script **extracts the coordinates** of the **thumb tip (ID: 4)** and **index finger tip (ID: 8)**.  
- The **distance** between these two points determines the volume level.  

### 4️⃣ Calculating Distance  
- The Euclidean distance formula is used to calculate the **distance between the two fingers**:  

### 5️⃣ Mapping Distance to Volume  
- The distance is **mapped** to the system volume range using interpolation.  
- **Minimum distance** = **Minimum volume**  
- **Maximum distance** = **Maximum volume**  

### 6️⃣ Adjusting System Volume  
- If the **pinky finger is down**, the volume is set using Pycaw.  
- If the pinky is **up**, the system ignores volume changes to avoid accidental adjustments.  

### 7️⃣ Visual Indicators  
- A **volume bar** appears on the screen to indicate current volume level.  
- If volume changes, the bar turns **green**; otherwise, it remains **blue**.  

### 8️⃣ FPS Calculation  
- The script calculates **frames per second (FPS)** to monitor performance.  

### 9️⃣ Continuous Loop & Exit  
- The program runs continuously until the user **closes the window** or stops execution manually.  
