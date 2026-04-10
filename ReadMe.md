# MENG3540: Parallel Programming Workflow
**Object Detection & Instance Segmentation on GPU Edge Device**

### 1) Problem Statement
[cite_start]The objective of this project is to develop a workflow for AI object detection and segmentation[cite: 71]. [cite_start]AI inferencing relies heavily on massive parallel matrix multiplications[cite: 81]. Running these workloads on a standard CPU creates severe processing bottlenecks. [cite_start]By utilizing hardware accelerators, we can process live camera feeds in real-time, enabling edge devices to act independently in industrial environments[cite: 81].

### 2) Hardware & Software Rationale
* [cite_start]**Hardware (NVIDIA Jetson Orin Nano):** Selected because it provides a dedicated Tegra GPU optimized for edge computing, offering the parallel processing power needed for real-time video feeds[cite: 74].
* [cite_start]**Software Framework (PyTorch & TensorRT):** PyTorch provides the neural network foundation, while TensorRT acts as a critical C++ compiler to optimize the math for the Tegra architecture[cite: 75].
* [cite_start]**Pre-Trained Models (YOLOv8n & YOLOv8n-seg):** The YOLO architecture is optimized for real-time embedded applications because of its single-pass detection, making it significantly faster than traditional multi-stage models[cite: 75].
