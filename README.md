# darknet-cpp-windows

Windows support for Darknet-cpp. This repository provides visual studio project files for Darknet-cpp. This repository does not require additional libraries like pthread, and provides all requirements integrated.

- For 2013 Visual Studio
- Needs CUDA 8.0 (and its environment settings correctly defined)

## Steps to build darknet-cpp-windows:

- Download the darknet-cpp port, from 

https://github.com/prabindh/darknet

- At the same level as the darknet folder, clone or download the darknet-cpp-windows sources

https://github.com/prabindh/darknet-cpp-windows

- Copy the "common" folder from Nvidia GPU Computing Toolkit into darknet-cpp-windows\darknet\ folder.

- Open the below solution file in Visual Studio

darknet-cpp-windows\darknet\darknet.sln

- Build the project arapaho, which will also build the darknet project dependency

- Copy the required data, weight, cfg and input image file for detection into the arapaho folder. All the files need to be named as {input.cfg, input.data, input.jpg, input.weights}. The names can be changed in the darknet\arapaho\test.cpp file.

- Run the generated binary arapaho.exe, for detection, from 

darknet-cpp-windows\bin\win64\$(Configuration)\arapaho.exe

- This will run the arapaho C++ wrapper, and generate output for the provided image.