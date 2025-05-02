![Project Status](https://img.shields.io/badge/Project%20Status-ongoing-orange)

# 🧠 YOLOv5 - American Sign Language (ASL) Letters Detection

This project leverages **YOLOv5** to detect and classify hand gestures of American Sign Language (ASL) letters:

**Supported Gestures:**  
- A  
- B  
- C  
- D  
- E  
- F  
- G  
- H  
- I  
- J  
- K  
- L  
- M  
- N  
- O  
- P  
- Q  
- R  
- S  
- T  
- U  
- V  
- W  
- X  
- Y  
- Z

---

### **Detection:**

<img src="demo/assets/prediction.jpg" alt="Model Performance" width="1200" height="600"/>

---
### **Model Performance:**

<div align="center">

<img src="demo/assets/results.png" alt="Model Performance" width="1000" height="300"/>

</div>


## 📦 Prerequisites

- Python 3.8+
- `pip` package manager

---

## ⚙️ Setup Instructions

### 1. Clone YOLOv5 Repository

```bash
git clone https://github.com/ultralytics/yolov5.git
cd yolov5
```

2. **Install Dependencies:**

    Make sure you are using Python 3.8. Then, install the required dependencies.

    ```bash
    pip install -r requirements.txt
    ```

3. **Label the Data:**

    We use the `labelImg` tool to annotate images for training.

    - Install `labelImg`:
      ```bash
      pip install labelImg
      ```

    - Open the tool and annotate images of the ASL gestures. Save annotations in YOLO format (i.e., `.txt` files with class and coordinates).
    
    - Example of a label file:
        ```
        0 0.5 0.5 0.2 0.3
        ```
        The numbers correspond to the class (0 for Hello, 1 for I Love You, etc.), followed by normalized center coordinates and width/height of the bounding box.

4. **Prepare Dataset:**

    Organize your dataset into the following folder structure:

    ```
    yolov5/
    ├── Data/
    │   ├── images/
    │   │   ├── train/
    │   │   └── val/
    │   └── labels/
    │       ├── train/
    │       └── val/
    ├── models/
    └── train.py
    ```

    - Place your training and validation images in `data/images/train/` and `data/images/val/`.
    - Place the corresponding annotation files (e.g., `.txt`) in `data/labels/train/` and `data/labels/val/`.

5. **Train the Model:**

    To train the model, run the following command:

    ```bash
    python train.py --img 640 --batch 16 --epochs 50 --data data.yaml --weights yolov5s.pt
    ```

    Here, `data.yaml` is the configuration file that contains paths to the dataset and class labels. You can create a `data.yaml` like this:

    ```yaml
    train: data/images/train
    val: data/images/val
    nc: 6
    names: ['A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I', 'J', 'K', 'L', 'M', 'N', 'O', 'P', 'Q', 'R', 'S', 'T', 'U', 'V', 'W', 'X', 'Y', 'Z']
    ```

6. **Predict using the Model:**

    After training, you can use the model to make predictions on new images:

### Make sure to move run.py and best.pt inside yolov5 clone directory
    
   ```bash
    python detect.py --weights runs/train/exp/weights/best.pt --img 640 --source path_to_your_image_or_directory
   ```

- Replace `path_to_your_image_or_directory` with the path to the image or directory where you want to perform predictions.

## Example Usage

To predict an image (e.g., `test.jpg`):

```bash
!python detect.py --weights runs/train/yolov5s_results/weights/best.pt --img 614 --conf 0.1 --source ./Data/test/images/
```
