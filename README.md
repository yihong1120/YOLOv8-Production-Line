# YOLOv8-PostProcessing-PRCurve

This repository contains code for post-processing techniques and PR curve visualization for object detection using YOLOv8. The project aims to improve object detection results through advanced post-processing methods and provides an analysis of precision and recall using PR curves.

The YOLOv8 model used in this project is sourced from the [Ultralytics repository](https://github.com/ultralytics/ultralytics).

## File Organisation

```
YOLOv8-PostProcessing-PRCurve/
├── images/
│   ├── yolov8_postprocess.png
│   └── PR-curves.png
├── scripts/
│   ├── yolo_label_converter.py
│   ├── yolo_inference_and_postprocessing.py
│   ├── pr_curve_validation.py
│   └── run_scripts.sh
├── README.md
└── requirements.txt
```

## Contents
- [Installation](#installation)
- [Label Conversion](#label-conversion)
- [Inference and Post-processing](#inference-and-post-processing)
- [PR Curve Validation](#pr-curve-validation)
- [Post-processing Flowchart](#post-processing-flowchart)
- [PR Curves](#pr-curves)
- [Run Scripts](run-scripts)

## Installation
1. Clone the repository:
```shell
git clone https://github.com/yihong1120/YOLOv8-PostProcessing-PRCurve.git
cd YOLOv8-PostProcessing-PRCurve
```

2. Install the required dependencies:
```shell
pip install -r requirements.txt
```

## Label Conversion
The **'yolo_label_converter.py'** file provides functions to convert YOLOv8 coordinates to regular bounding box coordinates. It reads text files containing bounding box information and converts them to a pickle file for further processing.

To use the label converter, modify the **'folder_path'** variable in the **'main()'** function to point to the directory containing the label files. Then run the script:

```shell
python scripts/yolo_label_converter.py
```

The converted labels will be saved as **'y_true.pkl'**.

## Inference and Post-processing
The **'yolo_inference_and_postprocessing.py'** file extends the YOLOv8 **'detect/val.py'** script. It performs object detection on images using a trained YOLOv8 model and applies post-processing techniques such as OCR and aspect ratio correction.

To use the inference and post-processing script, make sure to update the **'model'** and **'source'** variables in the **'predict()'** function with the appropriate paths. Then run the script:

```shell
python scripts/yolo_inference_and_postprocessing.py
```

The predicted results will be saved as **'y_preds.pkl'**.

## PR Curve Validation
The **'pr_curve_validation.py'** file calculates precision and recall values from the predicted and ground truth bounding boxes and plots PR curves for each class.

To validate the predicted results, make sure to have **'y_preds.pkl'** and **'y_true.pkl'** files in the repository. Then run the script:

```shell
python scripts/pr_curve_validation.py
```

The PR curves will be displayed in the console.

Feel free to explore and modify the code to suit your needs for post-processing and PR curve analysis in object detection using YOLOv8.

## Post-Process Flowchart
A flowchart illustrating the post-processing steps in **'yolo_inference_and_postprocessing.py'** can be found 
![here](https://github.com/yihong1120/YOLOv8-PostProcessing-PRCurve/blob/main/images/yolov8_postprocess.png)

The flowchart above illustrates the post-processing steps performed in the **'yolo_inference_and_postprocessing.py'** script. It shows the sequence of operations, including OCR, aspect ratio correction, and other specific post-processing tasks.

## PR Curve Visualization
A visualization of the PR curves generated by **'pr_curve_validation.py'** can be found 

![here](https://github.com/yihong1120/YOLOv8-PostProcessing-PRCurve/blob/main/images/PR-curves.png)

## Run Scripts
To conveniently run the necessary scripts, you can use the run_scripts.sh file provided in this repository. This bash script automates the execution of the required scripts in the correct order.

To run the scripts, navigate to the repository directory and execute the following command:

```shell
bash scripts/run_scripts.sh
```

The script will run the following scripts in sequence:

1. **'yolo_label_converter.py'**: Converts YOLOv8 labels to regular bounding box coordinates.
2. **'yolo_inference_and_postprocessing.py'**: Performs object detection and post-processing using YOLOv8.
3. **'pr_curve_validation.py'**: Calculates precision and recall values and plots PR curves.
Make sure to have the necessary input files in the repository before running the scripts.

Feel free to explore and modify the code to suit your needs for post-processing and PR curve analysis in object detection using YOLOv8.

## License
This project is licensed under the [AGPL-3.0](https://github.com/yihong1120/YOLOv8-PostProcessing-PRCurve/blob/main/LICENSE).
