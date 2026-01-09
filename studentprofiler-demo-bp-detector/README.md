# Student Profiler Demo - Behavioral Pattern Detector

This component of the Student Profiler system focusses on analyzing video feeds to detect and identify students and teachers in a classroom environment. It utilizes computer vision techniques for face recognition and template matching to track individuals.

## Features

- **Student Identification**: accurately detects and recognizes students' faces from video footage using pre-loaded images.
- **Teacher Detection**: Identifies the presence of a teacher in the classroom frame using template matching techniques.
- **Data Capture**: Includes utility scripts to extract frames from videos to build image datasets for teachers.
- **Real-time Visualization**: display the processed video feed with bounding boxes and labels identifying recognized individuals.

## Tech Stack

- **Language**: Python
- **Computer Vision**:
  - OpenCV (`cv2`)
  - Face Recognition (`face_recognition` library based on dlib)
- **Data Manipulation**: NumPy

## Algorithms & Approaches

### 1. Student Face Recognition

- **Library**: `face_recognition`
- **Process**:
  - **Encoding**: Converts reference images of students into 128-dimensional face encodings.
  - **Detection**: Finds face locations in video frames using HOG (Histogram of Oriented Gradients) or CNN.
  - **Comparison**: Compares the encodings of detected faces with known student encodings using Euclidean distance to find matches.

### 2. Teacher Detection

- **Method**: Template Matching
- **Process**:
  - Loads reference images of the teacher.
  - Scans the video frame to find regions that match the teacher's template image.
  - Uses `cv2.matchTemplate` with Normalized Cross-Correlation (`TM_CCOEFF_NORMED`) to identify the teacher's position.

## Project Structure

```markdown
studentprofiler-demo-bp-detector/
├── facial_recognition.py   # Main script for student identification
├── teacher.py              # Script for teacher detection via template matching
├── teacher_capture.py      # Utility to capture reference images from video
├── head_orientation.py     # Experimental script for head orientation/recognition
├── requirements.txt        # Python dependencies
├── haarcascade_eye.xml     # Haar cascade XML for eye detection
├── pictures/               # Reference images for students and teachers
│   ├── Teacher/            # Teacher reference images
│   └── [student images]    # Individual student images (1.png, 2.png, etc.)
└── videos/                 # Input directory for video files
```

## Setup Instructions

### Prerequisites

- Python 3.8+ (Python 3.10 recommended)
- CMake (required for dlib installation on some platforms)

### Installation

1. **Navigate to the directory:**

    ```bash
    cd studentprofiler-demo/studentprofiler-demo-bp-detector
    ```

2. **Create a virtual environment (Optional but recommended):**

    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows: venv\Scripts\activate
    ```

3. **Install dependencies:**

    ```bash
    pip install -r requirements.txt
    ```

    *Note: Installing `dlib` (a dependency of `face_recognition`) might require C++ build tools installed on your system.*

## Usage

### 1. Run Student Recognition

To detect and identify students in a video:

```bash
python facial_recognition.py
```

*Note: Ensure the `video_path` variable in the script is pointing to your target video file.*

### 2. Run Teacher Detection

To detect the teacher using template matching:

```bash
python teacher.py
```

### 3. Capture Teacher Images

To extract frames for teacher reference images from a video:

```bash
python teacher_capture.py
```

## Contributing

Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

## License

[MIT](../LICENSE)

## Developers

- **Dileepa Bandara** - *Initial work* - [dileepadev](https://github.com/dileepadev)

## Contact

For any inquiries, please contact:

- **Email**: [contact@dileepa.dev](mailto:contact@dileepa.dev)
- **GitHub**: [@dileepadev](https://github.com/dileepadev)

## Acknowledgements

- Uses the excellent face_recognition library.
- OpenCV community for computer vision tools.
- And all open-source contributors whose work made this project possible.
