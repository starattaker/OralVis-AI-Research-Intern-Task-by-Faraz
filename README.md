# Dental Panoramic X-ray Tooth Numbering

This repository contains the code and resources for training a YOLOv8 model to perform tooth numbering on dental panoramic X-ray images using the FDI system.

## Project Steps:

1.  **Dataset Loading and Unzipping**: The dataset, provided as a zip file (`ToothNumber_TaskDataset.zip`), was uploaded and unzipped to a local directory (`dataset`).
2.  **Dataset Copy**: A copy of the original dataset (`dataset_copy`) was created to perform cleaning and splitting without altering the original data.
3.  **Label File Cleaning**: Invalid annotation rows (those not following the 5-value YOLO format) were removed from the label files in `dataset_copy`.
4.  **Dataset Splitting**: The cleaned dataset (`dataset_copy`) was split into training (80%), validation (10%), and testing (10%) sets. The image and corresponding label files were copied into separate directories (`dataset_split/train`, `dataset_split/val`, `dataset_split/test`).
5.  **Data Configuration**: A `data.yaml` file was created to configure the dataset paths and class names for YOLO training, following the FDI tooth numbering system.
6.  **Environment Setup**: Necessary libraries, including `ultralytics`, were installed using `pip`. A `requirements.txt` file was generated to list the project dependencies.
7.  **Model Training**: A YOLOv8s model was trained on the prepared dataset using pretrained weights.
8.  **Model Evaluation**: The trained model was evaluated on the validation and test sets to assess its performance. Key metrics (Precision, Recall, mAP@50, mAP@50-95) and visualizations (Confusion Matrix, Training Curves, Sample Predictions) were generated.
9.  **Post-Processing (Optional)**: (Include details here if you implemented and want to mention the post-processing logic for anatomical correctness).

## Repository Contents:

*   `your_notebook_name.ipynb`: The Jupyter notebook containing all the code executed.
*   `data.yaml`: Data configuration file.
*   `requirements.txt`: List of Python dependencies.
*   `runs/detect/train/weights/best.pt`: The trained model weights.
*   `runs/detect/train/results.png`: Training curves plot.
*   `runs/detect/val*/confusion_matrix.png`: Confusion Matrix plot (replace `val*` with your validation run directory name).
*   `runs/detect/val*/PR_curve.png`, `runs/detect/val*/R_curve.png`, `runs/detect/val*/F1_curve.png`: Evaluation curve plots.
*   `sample_preds/preds*/`: Directory containing sample prediction images.

## Setup and Running:

1.  Clone the repository.
2.  Install dependencies using `pip install -r requirements.txt`.
3.  (Provide instructions on how to download and prepare the dataset if not included in the repo).
4.  Run the Jupyter notebook or relevant Python scripts to reproduce the training and evaluation.

## Training Command Example:
!yolo val model=runs/detect/train/weights/best.pt data=data.yaml split=val

!yolo val model=runs/detect/train/weights/best.pt data=data.yaml split=test
