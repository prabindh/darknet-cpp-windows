# darknet-cpp-windows

Windows support for Darknet-cpp. This repository provides visual studio project files for Darknet-cpp. This repository does not require additional libraries like pthread, and provides all requirements integrated. It supports Yolo v3.

- Support for 2015, 2017 Visual Studio versions, with one of below.
- Needs CUDA 8.0 (and its environment settings correctly defined, with Visual studio integration enabled), and CUDNN, OpenCV3 or
- Needs CUDA 9.1 (and its environment settings correctly defined, with Visual studio integration enabled), and CUDNN, OpenCV3
- Needs CUDA 10.1 (and its environment settings correctly defined, with Visual studio integration enabled), and CUDNN, OpenCV3.4

## Steps to build darknet-cpp-windows:

- Download the darknet-cpp port, from 

https://github.com/prabindh/darknet

- At the same level as the darknet folder, clone or download the darknet-cpp-windows sources

https://github.com/prabindh/darknet-cpp-windows

- Open the below solution file in Visual Studio

darknet-cpp-windows\darknet\darknet.sln (for CUDA10.1),

darknet-cpp-windows\darknet_cuda91\darknet_cuda91.sln (for CUDA9.1),

- Change the OpenCV folder path if needed (default expected to be 2 levels above, ..\..\opencv3\build\x64\vc15\lib)

- Build the project arapaho, which will also build the darknet project dependency

- Copy the required data, weight, cfg and input image file for detection into the arapaho folder. All the files need to be named as {input.cfg, input.data, input.jpg or input.mp4, input.weights}. The names can be changed in the darknet\arapaho\test.cpp file.

- Run the generated binary arapaho.exe, for detection, from 

darknet-cpp-windows\bin\win64\$(Configuration)\arapaho.exe

- This will run the arapaho C++ wrapper, and generate output for the provided image, and show each frame with detected regions in a Window. Example output below:

[YOLOV2]
....
Image data = 000001362EF87060, w = 992, h = 620
Detect: Resizing image to match network
l.softmax_tree = 0000000000000000, nms = 0.400000
Detected 1 objects
Box #0: x,y,w,h = [0.406386, 0.283149, 0.384096, 0.509924]
`

`
[YOLOV3]
...
 106 detection
Setup: net->n = 107
net->layers[0].batch = 1
Loading weights from input.weights...Done!
Setup: layers = 32, 32, 3
Warning: Read classes from cfg (80) > maxClasses (2)
Image expected w,h = [256][256]!
Setup: Done
Image data = 00000226B3EC3020, w = 640, h = 424
Detect: Resizing image to match network
==> Detected [3] objects in [3.275245] seconds
Box #0: center {x,y}, box {w,h} = [0.765709, 0.575041, 0.383576, 0.504763]
Label:horse
Box #1: center {x,y}, box {w,h} = [0.217989, 0.722828, 0.222815, 0.199334]
Label:dog
Box #2: center {x,y}, box {w,h} = [0.363993, 0.551002, 0.133328, 0.627906]
Label:person
cap.read failed/EoF - AV file input.jpg
`

The detected regions will be overlaid and shown in the Window that will open showing each frame.

For a brief about Arapaho C++ API, refer to https://github.com/prabindh/darknet/blob/master/arapaho/arapaho_readme.txt