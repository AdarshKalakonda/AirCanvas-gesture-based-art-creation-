# AirCanvas-gesture-based-art-creation-
This project represents an innovative Air Canvas, offering a novel approach to creative
expression through hand gestures. The system translates hand motions into artistic renderings by
tracking key landmarks on the hand, particularly the knuckles. Delving into the realm of air-based
writing, a complex domain within image processing and pattern recognition, the project capitalizes
on this fascination by developing a motion-to-text converter. This transformative capability is
achieved through the integration of Computer Vision (CV), Machine Learning (ML), and the
MediaPipe library.

# Algorithm

Step 1: Import Required Libraries
Import necessary libraries: cv2, numpy, mediapipe, and deque.

Step 2: Initialize Variables and Data Structures
Create deques for storing drawing points of different colors (bpoints, gpoints, rpoints, ypoints).
Define color indexes and initialize a kernel for image processing.
Set up a blank canvas (paintWindow) and draw buttons for color selection and clearing the screen.

Step 3: Initialize MediaPipe Hand Tracking
Load mpHands from mediapipe.solutions.hands
Initialize a webcam feed using cv2.VideoCapture(0).

Step 4: Process Webcam Feed in a Loop
Capture a frame from the webcam and get its dimensions.
Flip the frame horizontally to mirror real-time movements.
Convert the frame from BGR to RGB for MediaPipe processing.
Draw buttons for color selection and clearing the canvas.
Process the frame using hands.process(framergb) to detect hand landmarks.

Step 5: Detect Hand and Track Finger Movements
If hand landmarks are detected, extract landmark positions.
Identify the forefinger (landmark index 8) and thumb (landmark index 4).
Draw a small circle at the forefinger tip.

Step 6: Gesture-Based Drawing Mechanism
Check for "Air Tap" Gesture (Thumb Close to Forefinger):

If the thumb is near the forefinger (thumb[1] - center[1] < 30), start a new stroke by appending new deques.
Check for "Color Selection" or "Clear Screen" Gestures:

If the forefinger tip is within the top menu bar (center[1] <= 65), determine action:
Clear button pressed: Reset all drawing points and clear the canvas.
Color button pressed: Change the active drawing color.
Draw on Canvas Based on Selected Color:

Append the current forefinger position to the appropriate color deque.

Step 7: Render Drawing on Screen
Iterate through all points stored in color deques.
Draw continuous lines between consecutive points on both the live frame and paint window.
Display the updated frames using cv2.imshow().

Step 8: Exit Condition
If the user presses the 'q' key, exit the loop.
Release the webcam and destroy all OpenCV windows.
