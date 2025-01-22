## Memory (VRAMs) Requirements For Running MLLMs on GPUs
The memory requirements to use a **7 billion parameter MLLM** depend on several factors, including the **numerical precision (e.g., FP32, FP16)** and the task (training vs. inference). Here’s a detailed breakdown:

### How do you calculate Total Memory Requirements
#### Formula
**Total Memory (in bytes)** = Number of Parameters × Memory per Parameter
#### Steps
```diff
-Determine the Memory per Parameter:
```
* Convert bits per parameter to bytes per parameter:
  Bytes per Parameter = Bits per Parameter/8
```diff
-Multiply by the Total Number of Parameters:
```
* Multiply the memory per parameter (in bytes) by the total number of parameters in the model.
```diff
-Convert to GB:
```
* Since there are 1,073,741,824 bytes in 1 GB:
    Memory in GB = Total Memory in Bytes/1,073,741,824

#### Example for FP32 (32 Bits Per Parameter)
<img src="https://github.com/pallavig702/MultiModal-Knowledge-Base/blob/main/Images/MemReq2.png" alt="test" width="600"/>


### ​Breakdown for Other Formats
<img src="https://github.com/pallavig702/MultiModal-Knowledge-Base/blob/main/Images/MemReg4.png" alt="test" width="800"/>

 

## Additional Memory Requirements
Beyond the parameters themselves, you also need memory for:
#### 1) Intermediate Activations:
* Memory used during computations like attention, decoder states, etc.
* Adds approximately 30-50% more memory during inference and 2-3× more during training.

#### 2) Optimizer States (for Training):
* Optimizers like Adam or SGD require storing gradients and momentum for each parameter.
* This can double or triple the memory requirement during training.
#### 3) Batch Size:
* Larger batch sizes require more memory.
* For smaller batch sizes (e.g., 1-8), memory requirements remain manageable.
<img src="https://github.com/pallavig702/MultiModal-Knowledge-Base/blob/main/Images/MemReg5.png" alt="test" width="800"/>

## Minimum Hardware Requirements
To run a 7B parameter MLLM, you’ll need:
#### Inference:
* At least 24 GB VRAM for FP16.
* Quantization to INT8 or INT4 can reduce this to 10 GB or lower, enabling usage on consumer-grade GPUs like RTX 3060/3070.
#### Training:
* FP32: Requires 80 GB+ VRAM (e.g., A100, H100).
* FP16/BF16: Requires 40-60 GB VRAM (e.g., A6000 or multi-GPU setup).

## Optimizing Memory Usage
* **Quantization:** Convert the model to INT8 or INT4 for inference to reduce memory.
* **Offloading:** Use tools like **DeepSpeed ** or **bitsandbytes** to offload parts of the model to CPU memory.
* **Batch Size Reduction:** Lower the batch size to fit within hardware constraints.

