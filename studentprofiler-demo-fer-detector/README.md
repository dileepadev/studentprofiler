# Student Profiler Demo - Facial Emotion Recognition Detector

This component of the Student Profiler system is dedicated to detecting and analyzing student emotions from video feeds. It employs a Deep Learning model (Convolutional Neural Network) to recognize facial expressions and categorize them into specific emotional states.

## Features

- **Emotion Detection**: Recognizes 7 distinct diverse emotional states (Angry, Disgusted, Fearful, Happy, Neutral, Sad, Surprised) in real-time or from recorded video.
- **Model Training**: Includes scripts to train a custom CNN model on facial expression datasets.
- **Performance Evaluation**: Tools to evaluate model accuracy using confusion matrices and classification reports.
- **Data Logging**: Exports emotion statistics and aggregate counts to CSV files for further analysis.
- **Visualization**: Real-time video overlay with face bounding boxes and emotion labels.

## Tech Stack

- **Language**: Python
- **Deep Learning**:
  - TensorFlow / Keras
- **Computer Vision**:
  - OpenCV (`cv2`)
  - Haar Cascade Classifiers (*Face Detection*)
- **Data Analysis & Visualization**:
  - NumPy
  - Pandas
  - Scikit-learn
  - Matplotlib

## Algorithms & Approaches

### 1. Face Detection

- **Method**: Haar Feature-based Cascade Classifier.
- **Process**: Utilizes `haarcascade_frontalface_default.xml` to locate faces in each video frame. These regions of interest (ROIs) are then cropped and resized to 48x48 pixels for the model.

### 2. Emotion Classification (CNN)

- **Model Architecture**: Sequential Convolutional Neural Network.
  - **Convolutional Layers**: 4 layers (32, 64, 128, 128 filters) with ReLU activation to extract spatial features.
  - **Pooling Layers**: MaxPooling2D (2x2) to reduce dimensionality.
  - **Regularization**: Dropout layers (0.25, 0.5) to prevent overfitting.
  - **Fully Connected Layers**: Flatten followed by a Dense layer (1024 units) and an output Dense layer (7 units) with Softmax activation.
- **Optimization**: Adam optimizer with categorical crossentropy loss function.

## Project Structure

```markdown
studentprofiler-demo-fer-detector/
├── model_trainer.py        # Script to train the CNN model
├── model_tester.py         # Main script to run emotion detection on video
├── model_evaluator.py      # Script to evaluate model performance
├── display_values.py       # Helper script for data visualization
├── requirements.txt        # Python dependencies
├── haarcascades/           # OpenCV XML classifiers for face detection
├── model/                  # Saved model files (architecture .json and weights .h5)
├── data/                   # Dataset directory (train/test images)
├── csv/                    # Output directory for emotion statistics
└── videos/                 # Input directory for video files
```

## Setup Instructions

### Prerequisites

- Python 3.8+ (Python 3.10 recommended)
- A dataset of face images (e.g., FER-2013) organized in `data/train` and `data/test` folders if you intend to train the model.

### Installation

1. **Navigate to the directory:**

    ```bash
    cd studentprofiler-demo/studentprofiler-demo-fer-detector
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

## Usage

### 1. Detect Emotions in Video

To run the emotion detector on an existing video file or webcam:

1. Open `model_tester.py`.
2. Update the `cap` variable with your video path or set it to `0` for webcam.
3. Run the script:

    ```bash
    python model_tester.py
    ```

The script will generate `emotion_statistics.csv` and `emotion_count.csv` in the `csv/` folder.

### 2. Train the Model

To retrain the model with your own dataset:

1. Ensure your data is structured in `data/train` and `data/test` directories.
2. Run the training script:

    ```bash
    python model_trainer.py
    ```

This will save the new model architecture to `fer_model.json` and weights to `fer_model.h5`.

### 3. Evaluate the Model

To assess the model's performance:

```bash
python model_evaluator.py
```

This will display a confusion matrix and print a classification report.

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
- Added haarcascade frontalface_default.xml for face detection.
- OpenCV community for computer vision tools.
