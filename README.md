This Python script utilizes computer vision techniques to detect drowsiness and alertness levels of individuals in real-time by analyzing blink patterns. The system employs facial landmark detection to track the eyes and compute blink ratios, providing timely warnings when signs of drowsiness are detected.

**Features**
1. Real-time Monitoring: Continuous analysis of webcam feed to monitor blink patterns.
2. Blink Analysis: Precise calculation of blink ratios using facial landmarks.
3. Alert System: Instantaneous alerts when signs of drowsiness are detected.
4. Easy Integration: Simple integration with any Python environment supporting OpenCV, Dlib, and NumPy.
   
**Requirements**
1. Python 3.x
2. OpenCV (cv2)
3. Dlib
4. NumPy

**Installation**
1. Clone the repository
2. Install the required dependencies:
        pip install -r requirements.txt
3. Download the pre-trained facial landmark predictor file (shape_predictor_68_face_landmarks.dat) and place it in the project directory.

**Usage**
1. Run the Python script
2. Ensure your webcam is connected and properly configured.

3. Pay attention to the status displayed in the video feed:

  a. "Wake up!!!": Alert for prolonged periods of eye closure indicative of sleep.
  b. "Drowsy!!!": Warning for intermittent eye closures suggesting drowsiness.
  c. "Active!!!": Confirmation of alertness when no signs of drowsiness are detected.

**Acknowledgements**
OpenCV - Open Source Computer Vision Library
Dlib - Toolkit for Machine Learning and Computer Vision
Imutils - Convenience Functions for OpenCV and Dlib

**Project Explained**
This Python code utilizes OpenCV (cv2), Dlib, and NumPy for facial landmark detection and blink detection in real-time webcam video. Here's a breakdown of what the code does:

**Imports:**
cv2: OpenCV library for computer vision tasks.
numpy: Numerical computing library for handling arrays and mathematical operations.
dlib: Library for machine learning, specifically used here for face detection and facial landmark prediction.
face_utils from imutils: A collection of OpenCV and Dlib convenience functions to work with facial landmarks.
Initialization:

cap: Opens a connection to the default camera (index 0).
detector: Initializes a frontal face detector from Dlib.
predictor: Loads a pre-trained facial landmark predictor (shape_predictor_68_face_landmarks.dat).
Variables Initialization:

sleep, drowsy, active: Variables to track the state of the user (sleeping, drowsy, active).
status: A string to hold the current status message (e.g., "wake up!!!").
color: Color used for displaying the status text.
face_frame: A blank image for overlaying facial landmarks.
Functions:

compute(ptA, ptB): Calculates the Euclidean distance between two points.
blinked(a, b, c, d, e, f): Determines if the eyes are blinked based on the ratio of distances between specific facial landmarks.
Main Loop:

Captures frames from the webcam (cap.read()).
Converts each frame to grayscale for faster processing.
Detects faces in the grayscale frame using the detector.
For each detected face:
Draws a rectangle around the face on the original frame (frame).
Detects facial landmarks using the predictor.
Calculates blink status for left and right eyes using the blinked function.
Updates the status based on the blink status and duration of sleep/drowsiness/active state.
Draws the status text on the frame.
Draws circles on the face_frame to mark facial landmarks.
Displays the original frame (frame) and the face with landmarks (face_frame).
Terminates the loop when the "Esc" key (key code 27) is pressed.
