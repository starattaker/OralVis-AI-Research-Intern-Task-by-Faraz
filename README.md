Dental Panoramic X-ray Tooth Numbering
This repository contains the code and resources for training a YOLOv8 model to perform tooth numbering on dental panoramic X-ray images using the FDI system.

Project Steps:
Dataset Loading and Unzipping: The dataset, provided as a zip file (ToothNumber_TaskDataset.zip), was uploaded and unzipped to a local directory (dataset).
Dataset Copy: A copy of the original dataset (dataset_copy) was created to perform cleaning and splitting without altering the original data.
Label File Cleaning: Invalid annotation rows (those not following the 5-value YOLO format) were removed from the label files in dataset_copy.
Dataset Splitting: The cleaned dataset (dataset_copy) was split into training (80%), validation (10%), and testing (10%) sets. The image and corresponding label files were copied into separate directories (dataset_split/train, dataset_split/val, dataset_split/test).
Data Configuration: A data.yaml file was created to configure the dataset paths and class names for YOLO training, following the FDI tooth numbering system.
Environment Setup: Necessary libraries, including ultralytics, were installed using pip. A requirements.txt file was generated to list the project dependencies.
Model Training: A YOLOv8s model was trained on the prepared dataset using pretrained weights.
Model Evaluation: The trained model was evaluated on the validation and test sets to assess its performance. Key metrics (Precision, Recall, mAP@50, mAP@50-95) and visualizations (Confusion Matrix, Training Curves, Sample Predictions) were generated.
Post-Processing (Optional): (Include details here if you implemented and want to mention the post-processing logic for anatomical correctness).
Repository Contents:
your_notebook_name.ipynb: The Jupyter notebook containing all the code executed.
data.yaml: Data configuration file.
requirements.txt: List of Python dependencies.
runs/detect/train/weights/best.pt: The trained model weights.
dataset_split/: Directory containing the split dataset (consider if you want to upload the entire dataset or provide instructions on how to download and split it).
runs/detect/train/results.png: Training curves plot.
runs/detect/val*/confusion_matrix.png: Confusion Matrix plot (replace val* with your validation run directory name).
runs/detect/val*/PR_curve.png, runs/detect/val*/R_curve.png, runs/detect/val*/F1_curve.png: Evaluation curve plots.
sample_preds/preds*/: Directory containing sample prediction images.
Setup and Running:
Clone the repository.
Install dependencies using pip install -r requirements.txt.
(Provide instructions on how to download and prepare the dataset if not included in the repo).
Run the Jupyter notebook or relevant Python scripts to reproduce the training and evaluation.
Training Command Example:

[28]
37s
!yolo val model=runs/detect/train/weights/best.pt data=data.yaml split=val
!yolo val model=runs/detect/train/weights/best.pt data=data.yaml split=test
Ultralytics 8.3.189 🚀 Python-3.12.11 torch-2.8.0+cu126 CUDA:0 (Tesla T4, 15095MiB)
Model summary (fused): 72 layers, 11,137,968 parameters, 0 gradients, 28.5 GFLOPs
val: Fast image access ✅ (ping: 0.0±0.0 ms, read: 2283.0±444.8 MB/s, size: 56.5 KB)
val: Scanning /content/dataset_split/val/labels.cache... 49 images, 0 backgrounds, 0 corrupt: 100% ━━━━━━━━━━━━ 49/49 974032.7it/s 0.0s
                 Class     Images  Instances      Box(P          R      mAP50  mAP50-95): 100% ━━━━━━━━━━━━ 4/4 0.90it/s 4.4s
                   all         49       1381       0.91      0.937      0.957      0.686
           Canine (13)         45         45      0.879      0.933      0.956      0.662
           Canine (23)         45         45      0.896      0.958      0.959      0.647
           Canine (33)         48         48      0.954      0.979      0.986      0.691
           Canine (43)         48         48      0.913      0.979      0.962      0.719
  Central Incisor (21)         46         46      0.922      0.957      0.983      0.719
  Central Incisor (41)         48         49      0.932      0.835      0.902      0.457
  Central Incisor (31)         48         48      0.954      0.917      0.969       0.56
  Central Incisor (11)         46         46       0.92          1      0.988      0.705
      First Molar (16)         43         43       0.91      0.953      0.962      0.813
      First Molar (26)         41         41      0.941      0.976      0.976       0.74
      First Molar (36)         36         36      0.913      0.944      0.962      0.786
      First Molar (46)         39         39      0.934      0.949      0.975        0.8
   First Premolar (14)         41         41       0.88      0.878      0.945      0.597
   First Premolar (34)         47         47      0.905      0.936       0.97      0.731
   First Premolar (44)         46         46      0.917      0.978      0.971      0.722
   First Premolar (24)         42         42      0.975      0.924      0.984      0.618
  Lateral Incisor (22)         46         46      0.875      0.909      0.955      0.699
  Lateral Incisor (32)         48         48      0.972      0.917      0.967      0.648
  Lateral Incisor (42)         48         48      0.858      0.882      0.904      0.569
  Lateral Incisor (12)         47         47      0.894      0.894      0.929       0.59
     Second Molar (17)         45         45      0.824      0.956      0.917      0.671
     Second Molar (27)         44         44      0.852      0.932      0.942      0.729
     Second Molar (37)         39         39      0.851      0.974      0.935       0.74
     Second Molar (47)         40         40      0.907       0.95      0.963      0.818
  Second Premolar (15)         42         42      0.885      0.917       0.91      0.622
  Second Premolar (25)         43         43      0.965      0.953      0.983      0.708
  Second Premolar (35)         44         44      0.913      0.956      0.979      0.697
  Second Premolar (45)         45         45      0.968          1      0.995      0.772
      Third Molar (18)         34         34      0.882      0.878      0.913      0.533
      Third Molar (28)         36         36      0.861      0.861      0.927      0.596
      Third Molar (38)         36         36      0.938      0.944      0.972      0.774
      Third Molar (48)         34         34      0.929      0.971      0.989      0.816
Speed: 2.8ms preprocess, 26.4ms inference, 0.0ms loss, 8.1ms postprocess per image
Results saved to runs/detect/val3
💡 Learn more at https://docs.ultralytics.com/modes/val
Ultralytics 8.3.189 🚀 Python-3.12.11 torch-2.8.0+cu126 CUDA:0 (Tesla T4, 15095MiB)
Model summary (fused): 72 layers, 11,137,968 parameters, 0 gradients, 28.5 GFLOPs
val: Fast image access ✅ (ping: 0.0±0.0 ms, read: 1439.6±385.1 MB/s, size: 74.4 KB)
val: Scanning /content/dataset_split/test/labels.cache... 51 images, 0 backgrounds, 0 corrupt: 100% ━━━━━━━━━━━━ 51/51 713031.7it/s 0.0s
                 Class     Images  Instances      Box(P          R      mAP50  mAP50-95): 100% ━━━━━━━━━━━━ 4/4 0.84it/s 4.7s
                   all         51       1436      0.863      0.897      0.918      0.631
           Canine (13)         48         48      0.845      0.896        0.9      0.595
           Canine (23)         47         48      0.824      0.896      0.889      0.589
           Canine (33)         49         49      0.846      0.897      0.885      0.628
           Canine (43)         49         49      0.833      0.914      0.888      0.601
  Central Incisor (21)         45         45      0.872      0.911      0.943      0.678
  Central Incisor (41)         50         50       0.86      0.858      0.898      0.479
  Central Incisor (31)         49         49      0.778      0.858       0.84      0.471
  Central Incisor (11)         46         46       0.85      0.984      0.954      0.625
      First Molar (16)         46         46      0.839       0.87      0.882      0.623
      First Molar (26)         46         46      0.894      0.935      0.954      0.682
      First Molar (36)         41         42      0.877      0.952      0.953      0.786
      First Molar (46)         41         41       0.93          1       0.98      0.779
   First Premolar (14)         46         46      0.951       0.87      0.958      0.576
   First Premolar (34)         44         44       0.83      0.886      0.914        0.6
   First Premolar (44)         46         46      0.881       0.87      0.888      0.616
   First Premolar (24)         41         41      0.844      0.854      0.888      0.586
  Lateral Incisor (22)         46         47      0.876      0.872      0.916      0.602
  Lateral Incisor (32)         47         47       0.81      0.817       0.86      0.484
  Lateral Incisor (42)         49         49      0.847      0.776      0.868      0.509
  Lateral Incisor (12)         46         46      0.887      0.935      0.942      0.596
     Second Molar (17)         45         45      0.801      0.933      0.939      0.721
     Second Molar (27)         46         46      0.905      0.957      0.961      0.673
     Second Molar (37)         43         43      0.806      0.953      0.906      0.746
     Second Molar (47)         44         44      0.855      0.864      0.907      0.739
  Second Premolar (15)         46         46      0.918      0.977      0.941      0.658
  Second Premolar (25)         42         42      0.878      0.856      0.929      0.639
  Second Premolar (35)         43         43      0.832      0.922      0.932      0.684
  Second Premolar (45)         45         45      0.898      0.911      0.926      0.679
      Third Molar (18)         39         39      0.836      0.897      0.926      0.562
      Third Molar (28)         42         42      0.909      0.857      0.928      0.608
      Third Molar (38)         38         38      0.897      0.868      0.944      0.686
      Third Molar (48)         38         38      0.913      0.868      0.921      0.701
Speed: 4.5ms preprocess, 14.4ms inference, 0.0ms loss, 6.2ms postprocess per image
Results saved to runs/detect/val4
💡 Learn more at https://docs.ultralytics.com/modes/val
