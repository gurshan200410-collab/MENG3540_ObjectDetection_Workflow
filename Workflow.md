# Workflow & Prototype Documentation

### Overview
This system processes a live camera feed through an accelerated AI pipeline. The data flow is as follows:
[cite_start]`USB Camera Feed -> Jetson RAM -> YOLOv8 TensorRT Engine (GPU) -> OpenCV Annotation -> Display`[cite: 109].

### Steps for System & Environment Setup
[cite_start]To ensure proper GPU utilization, we bypassed standard pip installations to avoid conflicting `cu13` desktop libraries[cite: 110].
1. **Purged Conflicting Libraries:** `pip3 uninstall -y nvidia-cublas-cu13 nvidia-cudnn-cu13`
2. **OS-Level Dependency Injection:** Installed `cuda-keyring` and used `apt-get` to natively install `cudss` into the Ubuntu OS.
3. [cite_start]**Hardware Acceleration:** Compiled the `.pt` models into highly optimized `.engine` files using the Jetson's native compiler[cite: 110]:
   `/usr/src/tensorrt/bin/trtexec --onnx=yolov8n.onnx --saveEngine=yolov8n.engine --fp16`
4. [cite_start]**Sudo Pipeline Bridge:** Implemented `sys.path.insert(1, ...)` in the Python pipeline to allow root access to custom libraries[cite: 110].

### Software Framework Details
We utilized YOLOv8 alongside NVIDIA's TensorRT. [cite_start]TensorRT fuzes neural network layers and quantizes the precision to FP16, allowing the PyTorch model to run directly on the Jetson's parallel cores rather than the CPU[cite: 111].

### Results & Observations
* **Baseline Observation:** Running the `.pt` file forced computations through the CPU, resulting in severe bottlenecks and low frame rates.
* [cite_start]**Accelerated Observation:** Deploying the TensorRT `.engine` file successfully shifted the workload to the GPU[cite: 77]. 
* [cite_start]**Metrics:** The live camera feed achieved 20+ FPS[cite: 76]. [cite_start]The `jtop` utility confirmed active GPU utilization and dedicated GPU memory allocation for the `yolov8n` and `yolov8n-seg` processes[cite: 77, 112].

*(Insert your two screenshots here: The one showing the 20+ FPS camera feed, and the jtop screenshot showing the GPU bar and the renamed process)*

### References
* NVIDIA Jetson AI Lab Documentation
* Ultralytics YOLOv8 Architecture Guide
* [cite_start]OpenCV Python Documentation [cite: 115]
