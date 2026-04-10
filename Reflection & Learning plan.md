# Reflection and Learning Plan

### A) Individual Reflection
* [cite_start]**New Concepts Learned:** I learned how to cross-compile standard AI models into hardware-specific engines (TensorRT) to leverage parallel GPU architectures[cite: 118]. [cite_start]I also learned how to manage low-level Linux systems and resolve dependency mismatches at the OS level[cite: 118].
* [cite_start]**Project Successes:** The implementation of the `setproctitle` library and the manual mapping of the COCO dataset to the TensorRT engine outputs were highly successful in producing a clean, professional visualization[cite: 121].
* **Challenges & Contributions:** A major challenge was the PyTorch/CUDA dependency mismatch caused by `pip` installing incompatible desktop libraries. [cite_start]My contribution to solving this was pivoting away from Python workarounds and fixing the missing `libcudss.so.0` dependency directly in the Linux kernel via the `cuda-keyring`[cite: 122].

### B) Individual Learning Plan
* [cite_start]**Knowledge Gaps:** While I successfully deployed a pre-trained model, I have a gap in knowledge regarding gathering, labeling, and training custom datasets from scratch[cite: 125].
* [cite_start]**Scaling for Industry:** To implement this in a real industrial manufacturing setting, relying on the pre-trained COCO dataset (which detects common objects) is insufficient[cite: 126]. [cite_start]It would require expertise in training custom models to detect specific mechanical defects (e.g., failed welds or missing components on an assembly line)[cite: 127]. [cite_start]Furthermore, it would require skills in bridging the Python software with physical Mechatronic hardware (like PLCs) to trigger physical sorting actions based on the AI's visual data[cite: 127].
* [cite_start]**Future Training:** I plan to explore the NVIDIA DeepStream SDK for managing multiple industrial camera feeds simultaneously and look into tools like Roboflow for custom dataset generation[cite: 128].
