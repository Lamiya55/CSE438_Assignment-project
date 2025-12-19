# Waste Detection on Instance Segmentation using Semi-Supervised Learning

---

##  EAST WEST UNIVERSITY  


**Project Title:** Waste Detection on Instance Segmentation  
**Course Code:** CSE438  
**Course Title:** Digital Image Processing
**Section:** 03 
**Group:** E  

---

###  Submitted by

| Student Name | ID |
|-------------|----|
| Lamiya Akter | 2022-2-60-055 |
| Mashfia Zaheen | 2021-3-60-191 |
| Sultan Mahmud Shuvo | 2021-3-60-207 |

---

###  Submitted to  
**Dr. Md Rifat Ahmmad Rashid**  
Assistant Professor  
Department of Computer Science & Engineering  



---

## Project Overview
This project focuses on **waste detection using instance segmentation** with modern YOLO-based segmentation models.  
To reduce the dependency on expensive pixel-level annotations, we apply **Semi-Supervised Learning (SSL)** techniques that leverage both labeled and unlabeled data.

We compare:
- Supervised baseline models
- Semi-supervised learning methods under a fixed dataset split protocol

---

---

##  Training and Evaluation Setup (Notebook-Based)

All experiments in this project were conducted using **separate Kaggle notebooks** instead of command-line training scripts.

### Notebook Organization
- One notebook was used for each baseline model:
  - `YOLOv8-Seg` notebook
  - `YOLOv11-Seg` notebook
  - `YOLOv12-Seg` notebook
- Separate notebooks were also used for semi-supervised learning experiments:
  - FixMatch
  - MixMatch
  - Mean Teacher

Each notebook contains:
- Dataset loading and preprocessing
- Model initialization
- Training loop execution
- Validation and test evaluation
- Metric reporting (loss, mAP, IoU)
- Visualization of training and validation curves

---

##  Baseline Training (Notebook Workflow)

The baseline training workflow inside each notebook followed these steps:

1. Load the waste detection dataset using a YOLO segmentation configuration file.
2. Initialize the respective YOLO segmentation model (Yolov8, Yolov11, or Yolov12).
3. Train the model using **only labeled training data**.
4. Monitor training and validation loss during epochs.
5. Save the best-performing model weights.
6. Evaluate the trained model on the test split.

This workflow was repeated independently for YOLOv8-Seg, YOLOv11-Seg, and YOLOv12-Seg.

---

##  Semi-Supervised Learning Training (Notebook Workflow)

For SSL experiments, training was performed fully inside Kaggle notebooks using the required labeled/unlabeled split.

### FixMatch
- Weak and strong augmentations were applied within the notebook.
- Pseudo-labels were generated from weakly augmented unlabeled images.
- Only high-confidence predictions were used for training.
- The student model was trained using supervised and unsupervised losses.

### MixMatch
- Soft labels were predicted for unlabeled images.
- Predictions were sharpened to reduce entropy.
- Labeled and unlabeled samples were mixed using MixUp.
- The model was trained using the combined batch.

### Mean Teacher
- A student model was trained normally.
- A teacher model was maintained as an exponential moving average (EMA) of student weights.
- Teacher predictions were used as stable targets for unlabeled data.
- Student predictions were matched against teacher outputs.

---

## Evaluation (Notebook-Based)

Evaluation was also performed inside the notebooks:

- Models were evaluated on the **test split**.
- Metrics reported:
  - Mask mAP@0.5
  - Mask mAP@0.5–0.95
- Training and validation curves were visualized directly within the notebooks.
- Final metric values were exported or manually recorded for reporting.

---

##  Execution Environment: Kaggle

All notebooks were executed on **Kaggle Notebooks** with the following setup:
- GPU enabled (Kaggle accelerator)
- Python environment with required libraries installed
- Training, validation, and evaluation performed within the notebook environment

This notebook-based workflow ensured reproducibility and simplified experiment management without relying on external command-line execution.

---

