# Traffic signs data challenge

This challenge is part of Artificial Intelligence in Data Science - BMETE15MF75 course. <br>

This repo contains the task's solution and documentation.

## Task
The task is to build an algorithm for prohibitory traffic sign recognition.

## Data
### Data expanding
Twenty images are provided as training set for building and fine-tuning a model.Taking screenshots or using google-streetview Python module are suggested to add more images, however, I expanded the size of the set by augmenting the data.
For augmentation, three methods were used:
<ol>
  <li>Flipping <i>(20 images became 40)</i>.</li>
  <li>Blurring <i>(for the 40 images resulted from 1)</i>.</li>
  <li>Adding noise with increasing brightness <i>(for the 40 images resulted from 1)</i>.</li>
</ol>

Accordingly, the overall size of the set is 120 [images](./data/training_images) (*[split](./data/data_split.xlsx): 70 train, 10 validation and 40 test*). <br>
A note to keep in mind here, that augmentation has some drawbacks:
<ul>
  <li>It might cause model overfitting as a result of instances duplication.</li>
  <li>The overll number of images might not be enough.</li>
  <li>In case of traffic scene/signs, some augmentation methods might corrupt the data, e.g. Vertical flipping, rotation (with angle), etc.</li>
</ul>

On the other hand, data augmentation is a fast way to expand data (e.g. double and triple) with the minimum amount of effort compared to other manual methods like: screenshots collecting.

### Labels
Data consists of six unbalanced distributed categories:
<ul>
  <li>A: No turn</li>
  <li>B: Speed limit</li>
  <li>C: Road closed</li>
  <li>D: No entry</li>
  <li>E: No stop/park</li>
  <li>F: Others</li>
</ul>

### Annotation
Since the provided data is not from a standard dataset, annotation was missing. To solve this, I used [Makesense](www.makesense.ai) for manual annotation. The tool provides option to choose the proper format for the [annotations](./data/annotation/), i.e. YOLO, VOX XML and CSV.

## Model
To tackle this task, I trained the infamous object detection and recognition model [YOLOv5](https://github.com/ultralytics/yolov5) on the traffic signs data using its pretraining weights. To do so, I followed the available instruction on its implementation repository.

## Implementation
The data augmentation and model training can be found in this [notebook](./implementation/AI_in_DS_TrafficSigns_HW_Q7WKU4_Modafar.ipynb).

### Results
<ul>
  <li><a href="./data/training_results/feature_extraction">Feature extraction</a></li>
  <li><a href="./data/training_results/finetune">Fine-tuning</a></li>
  <li><a href="./data/training_results/validation">Validation</a></li>
  <li><a href="./data/training_results/detect_test">Detection</a></li>
</ul>
