## Memory (VRAMs) Requirements For Running MLLMs on GPUs
The memory requirements to use a **7 billion parameter MLLM** depend on several factors, including the **numerical precision (e.g., FP32, FP16)** and the task (training vs. inference). Here’s a detailed breakdown:
### Memory Requirements for Parameters
![test](https://github.com/pallavig702/MultiModal-Knowledge-Base/blob/main/Images/MemReq1.png)

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
![test2](https://github.com/pallavig702/MultiModal-Knowledge-Base/blob/main/Images/MemReq2.png)

### ​Breakdown for Other Formats
<img src="https://github.com/pallavig702/MultiModal-Knowledge-Base/blob/main/Images/MemReg4.png" alt="test" width="800"/>

 

## Additional Memory Requirements
