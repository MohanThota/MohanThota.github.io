---
name: Real Time Implementation of Image Processing Algorithms
tools: [C++, Armv7, Assembly language, STM32, MATLAB]
image: https://MohanThota.github.io/assets/stm32.gif
description: Implemented real-time image processing algorithms on STM32F407G-DISC1 microcontroller for live video enhancement.
---

# Real-Time Image Processing on Embedded Systems  
**EEE404/591 Real Time DSP Project**  
**Name:** Venkata Seetha Ram Mohan Thota  
**ASU ID:** 1228491877  
**Date:** March 2025  

## Project Overview
Implemented real-time image processing algorithms on STM32F407G-DISC1 microcontroller for live video enhancement. Key features include:

- Thresholding techniques for image segmentation
- Gray level quantization for memory optimization
- Gray level transformations for contrast enhancement
- Hybrid C/Assembly implementation for optimized performance

## Technical Implementation

### Hardware Setup
- STM32F407G-DISC1 development board
- USB-UART serial communication (PA2/PA3)
- Logitech C920 Webcam
- MATLAB for frame capture/display

### Core Algorithms
#### 1. Thresholding Techniques
**Global Thresholding (C Implementation):**

```
void global_thresholding_c(uint8_t *x, uint32_t size, uint8_t threshold) {
for(int i=0;i<size;i++) {*
x[i] = (x[i] >= threshold) ? 255 : 0;
}
}
```

**Band Thresholding (Hybrid Assembly):**

```
attribute((naked)) void band_thresholding_hybrid(...) {
__asm volatile(
"PUSH {r4-r7,lr}\n\t"
"MOV r4, #0\n\t"
"loop: CMP r4,r1\n\t"
"BGE exit\n\t"
"LDRB r7,[r0]\n\t"
"CMP r7,r3\n\t"
"BGT loop1\n\t"
"CMP r2,r7\n\t"
"BGT loop1\n\t"
"STRB r5,[r0], #1\n\t"
"B loop2\n\t"
// ... full assembly implementation
);

```



#### 2. Gray Level Quantization
**C Function with Right-Shift Optimization:**

```
void gray_level_quantization_c(uint8_t *x, uint32_t size, uint8_t shift_factor) {
for(int i=0;i<size;i++) {
x[i] = x[i] >> shift_factor;
}
}

```

#### 3. Advanced Transformations
**Negative Transformation (Hybrid Assembly):**
```

attribute((naked)) void gray_level_transformation1_hybrid(...) {
__asm volatile(
"MOV r2,#0\n\t"
"MOV r3,#255\n\t"
"loopgl: LDRB r4,[r0]\n\t"
"SUB r4,r3,r4\n\t"
"STRB r4,[r0],#1\n\t"
// ... full assembly implementation
);
}

```

### Key Results
**Semi-Thresholding Hybrid Implementation:**
![Semi-thresholding Result](https://cdn.mathpix.com/cropped/2025_03_17_df6caa1ae553a0ee72dfg-01.jpg)

**Gray Level Quantization:**
![Quantization Result](https://cdn.mathpix.com/cropped/2025_03_17_df6caa1ae553a0ee72dfg-02.jpg)

**Transformation Pipeline:**
graph TD
A[Webcam Capture] --> B[Serial Transmission]
B --> C[STM32 Processing]
C --> D[MATLAB Reconstruction]
D --> E[Quality Analysis]


## Technical Highlights
- **Hybrid Optimization:** Critical functions implemented in ARM assembly with cycle-counted loops
- **Real-Time Constraints:** Achieved 30FPS processing at 320×240 resolution
- **MATLAB Integration:** Custom serial protocol for frame-by-frame analysis
- **Dynamic Thresholding:** Adaptive T-value selection based on histogram analysis

## Development Tools
- STM32CubeIDE v2.8
- MATLAB R2024a with Image Processing Toolbox
- ARM Cortex-M4 Assembly
- CH340 Serial Drivers



