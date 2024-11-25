# MultiModal-Knowledge-Base
## What are multimodals?
Multimodal MLLMs (Multimodal Large Language Models) are advanced AI systems that combine the capabilities of Large Language Models (LLMs)—like GPT, which processes and generates text—with the ability to handle multiple types of data modalities, such as images, audio, video, and more. These models enable richer and more versatile interactions by integrating and processing data from various formats simultaneously.

Here one simple diagram from the [source](https://medium.com/@tenyks_blogger/multimodal-large-language-models-mllms-transforming-computer-vision-76d3c5dd267f)
![test3](https://github.com/pallavig702/MultiModal-Knowledge-Base/blob/main/Images/MLLM_Architecture.png)
```diff
-There are small, medium and large models.
```
![test2](https://github.com/pallavig702/MultiModal-Knowledge-Base/blob/main/Images/MLLM3.png)

```diff
-Here are examples of open source and closed source models.
```
![test](https://github.com/pallavig702/MultiModal-Knowledge-Base/blob/main/Images/MLLM_s.png)

Key Takeaways:
Small models prioritize efficiency and cost-effectiveness, often deployed in resource-constrained environments.
Medium models offer a balance between performance and resource usage, making them suitable for general enterprise needs.
Large models push the boundaries of performance, handling complex and nuanced tasks but come with significant resource and cost demands.

Few more examples of small, medium and large models.


## To effectively use a MLLM (samll, medium or large) what needs to be understood?
For this you need to understand several aspects spanning concepts, technical skills, and application-specific considerations.Let's take example of MLLM LLaVA-NeXT-Video-72B or similar. Here's a structured guide:

1. Foundational Concepts
a. What is a Multimodal Model?
A multimodal model processes and integrates multiple types of data (e.g., text, images, video, audio) to generate outputs or make predictions.
Example: Combining video frames and natural language prompts for tasks like video summarization or question answering.
b. Architecture Basics
Backbone Model: The LLM (e.g., Qwen-72B) is responsible for text understanding.
Vision/Video Encoder: Processes visual data like images or video frames into embeddings that the LLM can interpret.
Cross-Modality Attention: Links modalities to allow seamless reasoning across them.
c. Supported Modalities
Understand which data types the model can handle:
Text: Natural language prompts and outputs.
Images: Single frames or image sequences.
Videos: Frame sequences processed over time.
Audio (optional): In some models, speech or sound integration.
2. Technical Prerequisites
a. Hardware Requirements
GPU Resources: Multimodal models are memory-intensive.
Know your available GPU type (e.g., L40, A100, H100) and VRAM capacity.
Disk Space: Large models and datasets may require hundreds of GBs.
b. Software and Libraries
Frameworks: PyTorch or TensorFlow (most LLMs are PyTorch-based).
Model-Specific Libraries: Hugging Face Transformers, OpenMMlab for vision, or DeepSpeed for distributed training/inference.
Utilities: nvidia-smi for monitoring GPU usage, gpustat, and efficient file handling tools.
c. Environment Setup
Familiarity with:
Virtual environments (e.g., Conda, Docker).
Model deployment platforms (e.g., Slurm, AWS, Azure).
Install required dependencies (e.g., CUDA, PyTorch).
3. Data Preparation
a. Input Data
Preprocessing:
Text: Tokenization.
Images: Resizing, normalization.
Videos: Frame extraction and sampling.
Alignment: Ensure proper alignment between modalities (e.g., corresponding captions for video clips).
b. Dataset Format
Use appropriate formats (e.g., JSON, CSV) and structures:
Text-only tasks: Plain text or tokenized data.
Multimodal tasks: Paired datasets, such as video and descriptions.
c. Annotation
If fine-tuning, annotated datasets are critical for supervised learning tasks.
4. Model Configuration
a. Model Fine-Tuning or Pre-trained Usage
Fine-Tuning: Requires annotated multimodal data and computational resources.
Pre-trained Usage: Fine-tuning may not be necessary if the model can generalize well to your use case.
b. Tokenizer Setup
Ensure the tokenizer matches the pre-trained model (e.g., Qwen tokenizer for LLaVA-NeXT).
c. Cross-Modality Integration
Know how to encode each modality and feed it into the model:
Text: Tokenized strings.
Video: Encoded frame sequences (e.g., via vision transformer).
5. Running the Model
a. Input Construction
Construct prompts that combine modalities appropriately.
Example: "Summarize this video: [video frames encoded]."
Frame batching to optimize GPU utilization.
b. Inference Workflow
Use APIs or scripts to run inference.
Monitor memory and utilization during runtime to avoid crashes.
c. Optimizations
Quantization (e.g., 4-bit or 8-bit) to save VRAM.
Distributed inference for multi-GPU setups.
6. Task-Specific Considerations
a. Common Multimodal Tasks
Video/Frame Understanding: Classification, object detection, summarization.
Text-Image Tasks: Captioning, Q&A based on images.
Text-Video Tasks: Temporal reasoning, narrative analysis.
b. Evaluation Metrics
Text Outputs: BLEU, ROUGE, or accuracy for classification.
Video Outputs: F1 score, IoU (Intersection over Union) for detections.
Ensure metrics align with task objectives.
7. Ethical and Practical Considerations
a. Bias and Fairness
Multimodal models may inherit biases from training data (e.g., skewed image or text content).
Ensure fair and balanced datasets.
b. Explainability
Multimodal reasoning is complex. Use visualization tools to interpret model decisions.
c. Data Privacy
Handle sensitive data (e.g., user videos) securely and comply with regulations like GDPR.
8. Troubleshooting
Common Issues
Out-of-Memory (OOM): Reduce batch size, apply quantization.
Model Errors: Ensure tokenizers and encoders match the model.
Low Accuracy: Fine-tune with domain-specific data.
