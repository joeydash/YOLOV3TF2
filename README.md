# YoloV3 in TensorFlow

## Usage

### Requirements

* Tensorflow 2.0
* opencv-python


```bash
pip install -r requirements.txt
```


### Convert pre-trained Darknet weights

```bash
# yolov3
wget https://pjreddie.com/media/files/yolov3.weights -O data/yolov3.weights
python convert.py

# yolov3-tiny
wget https://pjreddie.com/media/files/yolov3-tiny.weights -O data/yolov3-tiny.weights
python convert.py --weights ./data/yolov3-tiny.weights --output ./checkpoints/yolov3-tiny.tf --tiny
```

### Detection

```bash
# yolov3
python detect.py --image ./data/meme.jpg

# yolov3-tiny
python detect.py --weights ./checkpoints/yolov3-tiny.tf --tiny --image ./data/street.jpg

# webcam
python detect_video.py --video 0

# video file
python detect_video.py --video path_to_file.mp4 --weights ./checkpoints/yolov3-tiny.tf --tiny

# video file with output
python detect_video.py --video path_to_file.mp4 --output ./output.avi
```


The inputs are preprocessed images (see `dataset.transform_iamges`)

outputs are
```
yolo_nms_0: bounding boxes
yolo_nms_1: scores
yolo_nms_2: classes
yolo_nms_3: numbers of valid detections
```