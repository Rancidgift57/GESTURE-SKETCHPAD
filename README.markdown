# Gesture Sketchpad

Gesture Sketchpad is an innovative, interactive drawing application that enables users to create sketches on a virtual canvas using hand gestures captured via a webcam. By leveraging computer vision and machine learning, the application offers a seamless and intuitive drawing experience with features like freehand drawing, shape detection, eraser functionality, and multiple color options. This project utilizes **OpenCV** for video capture and image processing, **MediaPipe** for real-time hand tracking, and a machine learning model for shape prediction.

## Table of Contents
- [Features](#features)
- [Requirements](#requirements)
- [Installation](#installation)
- [Usage](#usage)
  - [Hand Gestures](#hand-gestures)
  - [Keyboard Shortcuts](#keyboard-shortcuts)
- [Project Structure](#project-structure)
- [How It Works](#how-it-works)
  - [Hand Tracking](#hand-tracking)
  - [Shape Detection](#shape-detection)
  - [Drawing and Erasing](#drawing-and-erasing)
- [Dependencies](#dependencies)
- [Running the Application](#running-the-application)
- [Troubleshooting](#troubleshooting)
- [Future Enhancements](#future-enhancements)
- [Contributing](#contributing)
- [License](#license)

## Features
- **Hand Gesture Drawing**: Draw on a virtual canvas by tracking the position of your index finger and thumb using a webcam.
- **Shape Detection Mode**: Activate shape detection with the 'B' key to recognize and replace freehand sketches with precise geometric shapes (e.g., circles, squares).
- **Eraser Functionality**: Use the 'E' key to toggle the eraser tool, which removes parts of the drawing with a white circle, preserving shape detection functionality.
- **Multiple Color Options**: Choose from various brush and pencil colors to enhance the creativity of your sketches.
- **Shape Drawing Activation**: Trigger shape detection by raising the index and middle fingers; revert to freehand doodling with the thumb and index finger.
- **Intuitive Controls**: Use keyboard shortcuts to toggle shape detection ('B'), start/stop detection ('D'/'S'), and clear the canvas ('C').

## Requirements
To run Gesture Sketchpad, ensure you have the following:
- **Hardware**:
  - A webcam (built-in or external) for capturing hand gestures.
  - A computer with a decent CPU/GPU for real-time processing.
- **Software**:
  - Python 3.8 or higher.
  - A compatible operating system (Windows, macOS, or Linux).
  - A code editor (e.g., VS Code, PyCharm) for modifying the source code (optional).

## Installation
1. **Clone the Repository**:
   ```bash
   git clone https://github.com/your-username/gesture-sketchpad.git
   cd gesture-sketchpad
   ```

2. **Set Up a Virtual Environment** (recommended):
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install Dependencies**:
   Install the required Python packages using the provided `requirements.txt` file:
   ```bash
   pip install -r requirements.txt
   ```

4. **Download Pre-trained Models** (if applicable):
   - Ensure the machine learning model for shape detection is placed in the `models/` directory. (Replace with actual model download instructions if applicable.)

5. **Verify Webcam Access**:
   - Ensure your webcam is connected and accessible by Python's OpenCV library.

## Usage
### Hand Gestures
- **Freehand Drawing**: Hold your thumb and index finger together to draw on the canvas. The application tracks the tip of the index finger for precise control.
- **Shape Detection**: Raise your index and middle fingers to activate shape detection mode (requires 'B' key to be toggled on).
- **Erasing**: Activate the eraser tool with the 'E' key and move your hand to cover unwanted parts of the drawing with a white circle.

### Keyboard Shortcuts
- **B**: Toggle shape detection mode on/off.
- **D**: Start shape detection (when in shape detection mode).
- **S**: Stop shape detection.
- **E**: Toggle eraser tool on/off.
- **C**: Clear the canvas.
- **Q**: Quit the application.

## Project Structure
```plaintext
gesture-sketchpad/
│
├── main.py                 # Main script to run the application
├── gesture_handler.py      # Handles hand gesture detection and processing
├── shape_detector.py       # Machine learning model for shape prediction
├── canvas.py               # Manages the virtual canvas and drawing logic
├── models/                 # Directory for pre-trained shape detection models
├── requirements.txt        # List of required Python packages
├── README.md               # This file
└── assets/                 # Optional: Images, icons, or other resources
```

## How It Works
### Hand Tracking
- **MediaPipe Hand Tracking**: The application uses Google's MediaPipe library to detect and track hand landmarks in real-time. It specifically tracks the index finger and thumb for drawing and the index and middle fingers for shape detection.
- **Webcam Input**: OpenCV captures video frames from the webcam, which are processed to identify hand gestures.

### Shape Detection
- **Activation**: Shape detection is toggled with the 'B' key and activated when the index and middle fingers are raised.
- **Machine Learning Model**: A pre-trained model (e.g., a convolutional neural network) predicts shapes like circles and squares from freehand sketches.
- **Rendering**: Detected shapes are drawn on the canvas with precise geometric properties, replacing the original sketch.

### Drawing and Erasing
- **Drawing**: The canvas tracks the index finger's position to draw lines or shapes in the selected color.
- **Erasing**: The eraser tool draws a white circle over the canvas at the hand's position, effectively removing parts of the drawing.
- **Color Selection**: Users can switch between colors using a predefined palette (implementation details depend on the UI).

## Dependencies
The project relies on the following Python packages (listed in `requirements.txt`):
```plaintext
opencv-python==4.5.5.64
mediapipe==0.8.9.1
numpy==1.21.5
tensorflow==2.8.0  # For shape detection model (adjust version as needed)
```
Install them using:
```bash
pip install -r requirements.txt
```

## Running the Application
1. Activate the virtual environment (if used):
   ```bash
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

2. Run the main script:
   ```bash
   python main.py
   ```

3. Position your hand in front of the webcam and use the gestures and keyboard shortcuts to interact with the canvas.

4. Press 'Q' to exit the application.

## Troubleshooting
- **Webcam Not Detected**:
  - Ensure your webcam is connected and not being used by another application.
  - Check OpenCV's webcam index (default is 0; try 1 or 2 if needed).
- **Hand Tracking Issues**:
  - Ensure proper lighting and a clear view of your hand.
  - Update MediaPipe to the latest version if tracking is inconsistent.
- **Shape Detection Not Working**:
  - Verify that the pre-trained model is correctly placed in the `models/` directory.
  - Check if the 'B' key has been toggled to enable shape detection.
- **Performance Issues**:
  - Reduce the webcam resolution in `main.py` to improve frame rate.
  - Ensure your system meets the hardware requirements.

## Future Enhancements
- **Advanced Shape Detection**: Support for more complex shapes (e.g., triangles, polygons).
- **Color Palette UI**: Implement a graphical interface for selecting colors.
- **Undo/Redo Functionality**: Add support for undoing and redoing actions.
- **Gesture Customization**: Allow users to define custom gestures for different actions.
- **Save/Load Sketches**: Enable saving sketches as images or loading previous sketches.

## Contributing
Contributions are welcome! To contribute:
1. Fork the repository.
2. Create a new branch (`git checkout -b feature-name`).
3. Make your changes and commit (`git commit -m "Add feature-name"`).
4. Push to the branch (`git push origin feature-name`).
5. Open a pull request with a detailed description of your changes.

Please ensure your code follows the project's coding style and includes appropriate tests.

## Output
![Image](https://github.com/user-attachments/assets/e6e16bb0-6a2b-40ea-b2ac-2a0e9ad598ad)
![Image](https://github.com/user-attachments/assets/f21d5504-57d8-471c-a7ad-dacbcb73f32c)
![Image](https://github.com/user-attachments/assets/3b285051-a709-477d-89f1-29c6c63feabc)
![Image](https://github.com/user-attachments/assets/a0dc22dd-3512-4968-ac46-e71d6a88bac8)
![Image](https://github.com/user-attachments/assets/a135cb7c-471b-4fdc-a0de-e55496b4db55)
![Image](https://github.com/user-attachments/assets/4a40b0fe-ff71-40cd-a735-b6a197de89d6)
---
*Created by Nikhil Nair on November, 2024.*
