
Download the weights to ./data, e.g. from: https://github.com/AlexeyAB/darknet/releases/download/darknet_yolo_v4_pre/yolov4-tiny.weights

Switch to a virtual environment that has tensorflow 2.3.0 installed
python save_model.py --weights ./data/yolov4-tiny.weights --output ./checkpoints/yolov4-tiny-416 --input_size 416 --model yolov4 --tiny --framework tflite

Optional: Change the representative_data_gen function in convert_tflite.py to use a real dataset instead of the randomly generated data.

Switch to a virtual environment with tf2.5 or newer
python convert_tflite.py --weights ./checkpoints/yolov4-tiny-416 --output ./checkpoints/yolov4-tiny-416-int8.tflite --quantize_mode int8

You can now use the xformer like this:
path/to/xformer.py ./checkpoints/yolov4-tiny-416-int8.tflite ./checkpoints/yolov4-tiny-416-int8-xcore.tflite -v -p 5