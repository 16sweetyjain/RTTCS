# RTTCS
### Getting Started 
### Pip
```bash
# TensorFlow CPU
pip install -r requirements.txt
```
## Downloading Official Pre-trained Weights
Download pre-trained yolov4.weights file: https://drive.google.com/open?id=1cewMfusmPjYWbrnuJRuKhPMwRe_b9PaT

## Using Custom Trained YOLOv4 Weights
Download license plate trained custom weights: https://drive.google.com/file/d/1EUPtbtdF0bjRtNjGv436vDY28EN5DXDH/view?usp=sharing

Copy and paste custom.weights file into the 'data' folder.
Copy and paste custom.names into the 'data/classes/' folder.

For custom model to work, change line 14 of core/config.py from coco.name to custom.names.

## YOLOv4 Using Tensorflow 
To implement YOLOv4 using TensorFlow, first we convert the .weights into the corresponding TensorFlow model files and then run the model.
```bash
# Convert darknet weights to tensorflow
## yolov4
python save_model.py --weights ./data/yolov4.weights --output ./checkpoints/yolov4-416 --input_size 416 --model yolov4 

# Run yolov4 on video
python detect_video.py --weights ./checkpoints/yolov4-416 --size 416 --model yolov4 --video ./data/video/input_video.mp4 --output ./detections/recognition.avi 
```


## Custom YOLOv4
### Convert custom weights to tensorflow
```bash
python save_model.py --weights ./data/custom.weights --output ./checkpoints/custom-416 --input_size 416 --model yolov4 
```
### Run custom yolov4 tensorflow model
```bash
python detect_video.py --weights ./checkpoints/custom-416 --size 416 --model yolov4 --video ./data/video/input_video.mp4 --output ./detections/recognition.avi
```

### Count Total Objects
#### To count total objects all that is needed is to add the custom flag "--count" to your detect.py or detect_video.py command.

To count number of objects per class use following command
```bash
python detect_video.py --weights ./checkpoints/yolov4-416 --size 416 --model yolov4 --video ./data/video/input_video.mp4 --output ./detections/recognition.avi --count
```
To count total number of objects, set the byClass=False in line 146 of detect_video.py and use the above command.


