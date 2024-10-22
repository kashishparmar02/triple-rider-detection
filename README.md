# Triple-Rider Detection

## Project Overview

Triple-Rider Detection is a computer vision project that detects motorcycles with more than two riders and checks for helmet compliance. Additionally, it identifies if the motorcycle is being used on a mobile device. This project utilizes YOLOv8, trained on a custom dataset of over 6,000 images, to achieve high-performance detection.

## Table of Contents

- [Project Description](#project-description)
- [Installation Instructions](#installation-instructions)
- [Usage Instructions](#usage-instructions)
- [Dataset Information](#dataset-information)
- [Training Details](#training-details)
- [Preprocessing](#preprocessing)
- [Sample Output Images](#sample-output-images)


## Project Description

Triple-Rider Detection aims to enhance motorcycle safety by identifying whether a motorcycle has more than two riders and ensuring all riders are wearing helmets. The project also detects if the motorcycle is being used on a mobile device. The system uses YOLOv8 for object detection, providing real-time feedback on helmet compliance and usage status.

## Installation Instructions

1. **Clone the Repository:**

    ```bash
    git clone https://github.com/yourusername/triple-rider-detection.git
    cd triple-rider-detection
    ```

2. **Set Up the Environment:**

    Create a virtual environment and install dependencies:

    ```bash
    python -m venv env
    source env/bin/activate  # On Windows use: env\Scripts\activate
    pip install -r requirements.txt
    ```

3. **Install Roboflow Inference SDK:**

    ```bash
    pip install inference-sdk
    ```

## Usage Instructions

### Using the Roboflow Inference SDK

1. **Obtain a Roboflow API Key:**

    To use the Roboflow API, you need your own API key. Follow these steps:
    
    - Sign up for a Roboflow account at [Roboflow](https://roboflow.com/).
    - Create a new project and upload your dataset.
    - Retrieve your API key from the Roboflow dashboard.

2. **Update API Key and Model ID:**

    Replace the `YOUR_API_KEY`, `YOUR_IMAGE.jpg`, and `model_id` with your actual values in the code snippet below.

    ```python
    # import the inference-sdk
    from inference_sdk import InferenceHTTPClient

    # initialize the client
    CLIENT = InferenceHTTPClient(
        api_url="https://detect.roboflow.com",
        api_key="YOUR_API_KEY"  # Replace YOUR_API_KEY with your actual API key
    )

    # infer on a local image
    result = CLIENT.infer("path/to/your/image.jpg", model_id="3riders/2")
    ```

3. **Run Inference:**

    Save the above code to a Python file and execute it to perform inference on your image.

## Dataset Information

The dataset used for training includes a custom collection of images created specifically for this project. It is divided as follows:

- **Train Set**: 87% (5,295 images)
- **Validation Set**: 8% (514 images)
- **Test Set**: 4% (248 images)

This custom dataset was designed to provide a diverse range of scenarios to improve the accuracy and robustness of the model in detecting motorcycles with more than two riders, helmet compliance, and mobile usage.

## Training Details

- **Model**: YOLOv8
- **Training Set Size**: 6,000 images
- **Performance Metrics**:
  - mAP: 81.7%
  - Precision: 80.8%
  - Recall: 75.0%

### Training Graphs


![](images/t.png)

## Preprocessing

- **Auto-Orient**: Applied
- **Resize**: Stretch to 640x640
- **Augmentations**:
  - Flip: Horizontal, Vertical
  - Rotation: 90° Clockwise, Counter-Clockwise
  - Crop: 0% Minimum Zoom, 22% Maximum Zoom
  - Rotation: Between -11° and +11°
  - Shear: ±12° Horizontal, ±12° Vertical

### Confusion Matrix

![Confusion Matrix](images/c.png)

## Sample Output Images

### Image 1

![Output Image 1](images/r1.png)

*Description: Example of motorcycle with more than two riders detected.*

### Image 2

![Output Image 2](images/fverw.png)

*Description: Example of helmet compliance detection.*

### Image 3

![Output Image 3](images/tr.png)

*Description: Example of detection results with bounding boxes and labels.*

### Image 4

![Mobile Detection](images/m.png)

*Description: Example of motorcycle detection with mobile usage.*



