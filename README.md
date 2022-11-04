# yolov5-object-detector

YOLOv5 object detction for weights.onnx

Input: cv2.imread("image1.jpg")
Output: list = [label, conf, box[x1, y1, x2, y2]]

Simple detect script for yolov5.onnx.(You can change weight.pt into weight.onnx by running export.py from yolov5.)
Reference from EscaticZheng/yolov5-onnx-inference and from detect.py in ultralytics/yolov5.
Inference per image.

Default is set to cpu.
To change into gpu, ctrl+f and check 'to run with gpu' line


## Requirements
**Check https://github.com/EscaticZheng/yolov5-onnx-inference**
numpy==1.22.3   
opencv-python==4.5.5  
torch==1.9.0+cu102  
torchvision==0.10.0+cu102  
onnxruntime-gpu==1.12.1  
**If you use cpu version, you can pip install torch, torchvision, and onnxruntime**


## detect.py
```python
# detect.py

run(input) # input = cv2.imread("image1.jpg")
# ...
def run(input)
    # ...
    output = []
    # ...
    return output 
```


## test_detect.py
You can check how it runs by
```python
python test_detect.py
```

```python
# test_detect.py

# input image
input = cv2.imread("image1.jpg")

# ...

# check the result
cv2.imwrite('test_cpu.jpg', input)
# ...
print(output)
```

```python
print(det)
```
will result on
```python
#        x1        y1        x2        y2          conf      label
tensor([[120.0000, 271.0000, 179.0000, 356.0000,   0.9326,   8.0000],
        [271.0000, 114.0000, 309.0000, 172.0000,   0.9247,   8.0000],
        [152.0000, 433.0000, 227.0000, 518.0000,   0.9240,   8.0000],
        [305.0000, 353.0000, 367.0000, 432.0000,   0.9106,   8.0000],
        [ 35.0000, 248.0000,  96.0000, 326.0000,   0.8850,   8.0000],
        [325.0000, 144.0000, 375.0000, 191.0000,   0.8793,   8.0000],
        [ 49.0000, 386.0000, 108.0000, 452.0000,   0.8015,  11.0000],
        [200.0000, 217.0000, 254.0000, 309.0000,   0.7752,  11.0000],
        [200.0000, 219.0000, 255.0000, 309.0000,   0.7310,   7.0000],
        [248.0000, 419.0000, 321.0000, 509.0000,   0.7031,  11.0000]])
```
and
```python
print(output)
```
will result on
```python
# label conf box[x1, y1, x2, y2]
[[8, 0.9326, [120, 271, 179, 356]], [8, 0.9247, [271, 114, 309, 172]], [8, 0.924, [152, 433, 227, 518]], [8, 0.9106, [305, 353, 367, 432]], [8, 0.885, [35, 248, 96, 326]], [8, 0.8793, [325, 144, 375, 191]], [11, 0.8015, [49, 386, 108, 452]], [11, 0.7752, [200, 217, 254, 309]], [7, 0.731, [200, 219, 255, 309]], [11, 0.7031, [248, 419, 321, 509]]]
```
