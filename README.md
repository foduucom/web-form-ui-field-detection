# web-form-ui-field-detection
![](https://github.com/foduucom/web-form-ui-field-detection/blob/main/web-form-ui-field-detection%20banner.jpeg?raw=true)



## Overview
The web-form-Detect model is a yolov8 object detection model trained to detect and locate ui form fields in images. It is built upon the ultralytics library and fine-tuned using a dataset of annotated ui form images.

## Model Architecture
![](https://github.com/foduucom/web-form-ui-field-detection/blob/main/ui%20architecture.jpeg)

## Intended Use
The model is intended to be used for detecting details like Name, number, email, password, button, radio bullet, and so on fields in images. It can be incorporated into applications that require automated detection ui form fields from images.

## Performance
The model has been evaluated on a held-out test dataset and achieved the following performance metrics:

Average Precision (AP): 0.51 Precision: 0.80 Recall: 0.70 F1 Score: 0.71 Please note that the actual performance may vary based on the input data distribution and quality.

## How to Get Started with the Model
### To get started with the YOLOv8s object Detection model used for web ui detection, follow these steps:
```
pip install ultralyticsplus==0.0.28 ultralytics==8.0.43
```
### Load model and perform prediction:
```
from ultralyticsplus import YOLO, render_result
```
### load model
```
model = YOLO('foduucom/web-form-ui-field-detection')
```
### Set model parameters
```
model.overrides['conf'] = 0.25  # NMS confidence threshold
model.overrides['iou'] = 0.45  # NMS IoU threshold
model.overrides['agnostic_nms'] = False  # NMS class-agnostic
model.overrides['max_det'] = 1000  # maximum number of detections per image
```
### set image
```
image = '/path/to/your/document/images'
```
### perform inference
```
results = model.predict(image)
```
### observe results
```
print(results[0].boxes)
render = render_result(model=model, image=image, result=results[0])
render.show()
```
## Training Data
The model was trained on a diverse dataset containing images of web ui form data from different sources, resolutions, and lighting conditions. The dataset was annotated with bounding box coordinates to indicate the location of the ui form fields within the image.

Total Number of Images: 600 Annotation Format: Bounding box coordinates (xmin, ymin, xmax, ymax)

## Fine-tuning Process
* Pre-trained Model: TheError: Errors in your YAML metadata model were initialized with a pre-trained object detection backbone (e.g. YOLO).
* Loss Function: Mean Average Precision (mAP) loss was used for optimization during training.
* Optimizer: Adam optimizer with a learning rate of 1e-4.
* Batch Size:-1

### Contact 
For inquiries and contributions, please contact us at - [info@foduu.com](mailto:info@foduu.com)
