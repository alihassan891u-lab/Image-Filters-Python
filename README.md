# Image Filters Python: Comprehensive Image Processing Library

## 📋 Overview

A comprehensive Python library providing a collection of essential image filtering and processing algorithms. This project implements various classical and advanced image manipulation techniques using Python and OpenCV, enabling developers to apply professional-grade visual effects and transformations to images with simple, intuitive scripts.

---

## ✨ Features & Filters Included

### **Blur Filters**
| Filter | File | Description |
|--------|------|-------------|
| **Standard Blur** | `Blur_An_Image.py` | Basic image blur using averaging kernel |
| **Box Blur** | `Box_Blur_An_Image.py` | Box filter blur for quick smoothing effects |
| **Gaussian Blur** | `Gaussian_Blur_An_Image.py` | Professional Gaussian blur with smooth transitions |

### **Color & Tone Filters**
| Filter | File | Description |
|--------|------|-------------|
| **Grayscale** | `GrayScale_Filter_An_Image.py` | Convert color images to grayscale |
| **Brightness Control** | `Inc_or_Dec_Brightness_In_An_Image.py` | Increase or decrease image brightness |

### **Edge & Enhancement Filters**
| Filter | File | Description |
|--------|------|-------------|
| **Edge Enhance** | `Edge_Enhance_An_Image.py` | Enhance edge detection for clarity |
| **Contour Detection** | `Contour_An_Image.py` | Extract and highlight image contours |
| **Emboss Effect** | `Emboss_An_Image.py` | Create 3D embossed effect |

### **Advanced Filters**
| Filter | File | Description |
|--------|------|-------------|
| **Cartoonize** | `Cartoonize_An_Image.py` | Convert photo to cartoon-style artwork |
| **Custom Kernel Filter** | `Kernal_Filter_An_Image.py` | Apply custom convolution kernels |

---

## 🛠️ Technology Stack

| Component | Technology |
|-----------|-----------|
| **Language** | Python 3.x |
| **Primary Library** | OpenCV (cv2) |
| **Image Processing** | NumPy |
| **File I/O** | PIL/Pillow (optional) |
| **Environment** | Command Line / Jupyter Notebook |

---

## 📦 Installation & Setup

### Prerequisites:
```
- Python 3.6+
- pip (Python package manager)
- OpenCV library
```

### Step 1: Install Python
Ensure Python 3.6 or higher is installed on your system.

### Step 2: Install Required Libraries

Install OpenCV and NumPy:
```bash
pip install opencv-python numpy
```

Or install all dependencies:
```bash
pip install -r requirements.txt
```

### Step 3: Clone Repository
```bash
git clone https://github.com/alihassan891u-lab/Image-Filters-Python.git
cd Image-Filters-Python-main
```

### Step 4: Prepare Input Images
Place images you want to filter in the project directory or specify the path in the script.

---

## 🚀 Usage Guide

### Basic Usage Pattern

All filters follow a similar usage pattern. Here's the general structure:

```python
import cv2

# Read image
image = cv2.imread('path/to/image.jpg')

# Apply filter
# (specific implementation varies by filter)

# Save result
cv2.imwrite('output_filtered_image.jpg', filtered_image)

# Display (optional)
cv2.imshow('Filtered Image', filtered_image)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

---

## 📖 Filter Details & Examples

### **1. Blur Filter** 
**File**: `Blur_An_Image.py`
- **Purpose**: Apply basic blur to smooth image
- **Use Case**: Reduce noise, create soft effects
- **Implementation**: Averaging kernel
```bash
python Blur_An_Image.py
```

### **2. Box Blur Filter**
**File**: `Box_Blur_An_Image.py`
- **Purpose**: Fast blur using box kernel
- **Use Case**: Quick smoothing for performance
- **Implementation**: Box averaging
```bash
python Box_Blur_An_Image.py
```

### **3. Gaussian Blur**
**File**: `Gaussian_Blur_An_Image.py`
- **Purpose**: Professional smooth blur effect
- **Use Case**: Quality image smoothing, preprocessing
- **Implementation**: Gaussian kernel (σ-based)
- **Advantages**: Natural-looking blur, spatially smooth
```bash
python Gaussian_Blur_An_Image.py
```

### **4. Grayscale Conversion**
**File**: `GrayScale_Filter_An_Image.py`
- **Purpose**: Convert color to grayscale
- **Use Case**: B&W photography, preprocessing
- **Implementation**: Weighted RGB channel conversion
- **Formula**: Gray = 0.299R + 0.587G + 0.114B
```bash
python GrayScale_Filter_An_Image.py
```

### **5. Brightness Adjustment**
**File**: `Inc_or_Dec_Brightness_In_An_Image.py`
- **Purpose**: Increase or decrease brightness
- **Use Case**: Exposure correction, lighting adjustment
- **Implementation**: Pixel value addition/subtraction
```bash
python Inc_or_Dec_Brightness_In_An_Image.py
```

### **6. Edge Enhancement**
**File**: `Edge_Enhance_An_Image.py`
- **Purpose**: Enhance edges for clarity
- **Use Case**: Sharpening, detail enhancement
- **Implementation**: High-pass filtering
```bash
python Edge_Enhance_An_Image.py
```

### **7. Contour Detection**
**File**: `Contour_An_Image.py`
- **Purpose**: Extract and highlight contours
- **Use Case**: Object detection, outline extraction
- **Implementation**: Edge detection + contour finding
```bash
python Contour_An_Image.py
```

### **8. Emboss Effect**
**File**: `Emboss_An_Image.py`
- **Purpose**: Create 3D embossed appearance
- **Use Case**: Artistic effects, texture creation
- **Implementation**: Directional kernel convolution
```bash
python Emboss_An_Image.py
```

### **9. Cartoonize Effect**
**File**: `Cartoonize_An_Image.py`
- **Purpose**: Convert photo to cartoon style
- **Use Case**: Artistic rendering, creative effects
- **Implementation**: 
  - Bilateral filtering (edge preservation)
  - Edge detection
  - Color quantization
- **Advanced Feature**: Preserves important edges while smoothing colors
```bash
python Cartoonize_An_Image.py
```

### **10. Custom Kernel Filter**
**File**: `Kernal_Filter_An_Image.py`
- **Purpose**: Apply custom convolution kernels
- **Use Case**: Custom effects, specialized processing
- **Implementation**: General 2D convolution
- **Flexibility**: Define your own kernel matrix
```bash
python Kernal_Filter_An_Image.py
```

---

## 🔧 Advanced Usage

### Creating Custom Filters

You can create custom filters by defining your own kernels:

```python
import cv2
import numpy as np

# Read image
img = cv2.imread('image.jpg')

# Define custom kernel (3x3 example)
kernel = np.array([[-1, 0, 1],
                   [-2, 0, 2],
                   [-1, 0, 1]])

# Normalize kernel
kernel = kernel / kernel.sum() if kernel.sum() != 0 else kernel

# Apply filter
filtered = cv2.filter2D(img, -1, kernel)

# Save
cv2.imwrite('custom_filtered.jpg', filtered)
```

### Chaining Filters

Apply multiple filters sequentially:

```python
import cv2

img = cv2.imread('image.jpg')

# Apply multiple filters
img = cv2.GaussianBlur(img, (5, 5), 0)  # Blur
img = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)  # Grayscale
# ... apply more filters

cv2.imwrite('multi_filtered.jpg', img)
```

### Batch Processing

Process multiple images:

```python
import cv2
import os
from pathlib import Path

input_dir = 'input_images/'
output_dir = 'output_images/'

for filename in os.listdir(input_dir):
    if filename.endswith('.jpg'):
        img = cv2.imread(os.path.join(input_dir, filename))
        # Apply filter
        filtered = cv2.GaussianBlur(img, (5, 5), 0)
        # Save
        cv2.imwrite(os.path.join(output_dir, filename), filtered)
```

---

## 📁 Project Structure

```
Image-Filters-Python-main/
├── Blur_An_Image.py                    # Standard blur filter
├── Box_Blur_An_Image.py                # Box blur filter
├── Gaussian_Blur_An_Image.py           # Gaussian blur filter
├── Cartoonize_An_Image.py              # Cartoonize effect
├── Contour_An_Image.py                 # Contour detection
├── Edge_Enhance_An_Image.py            # Edge enhancement
├── Emboss_An_Image.py                  # Emboss effect
├── GrayScale_Filter_An_Image.py        # Grayscale conversion
├── Inc_or_Dec_Brightness_In_An_Image.py # Brightness adjustment
├── Kernal_Filter_An_Image.py           # Custom kernel filter
├── README.md                           # Documentation
├── LICENSE                             # Project license
└── requirements.txt                    # Dependencies
```

---

## 🎯 Use Cases

| Use Case | Recommended Filters |
|----------|-------------------|
| **Photo Enhancement** | Gaussian Blur, Edge Enhance, Brightness Control |
| **Artistic Effects** | Cartoonize, Emboss, Custom Kernels |
| **Image Analysis** | Grayscale, Contour Detection, Edge Enhance |
| **Preprocessing** | Gaussian Blur, Grayscale |
| **Creative Projects** | Cartoonize, Emboss, Custom Effects |
| **Object Detection** | Contour Detection, Edge Enhancement |

---

## 📊 Technical Specifications

### Image Processing Concepts

**Convolution Kernel**: Small matrix applied across image for filtering
**Gaussian Distribution**: Bell curve used for natural-looking blur
**Bilateral Filtering**: Preserves edges while blurring
**Contour**: Boundary between objects and background
**Kernel Convolution**: Element-wise multiplication and summation

### Performance Characteristics

| Filter | Speed | Quality | Memory |
|--------|-------|---------|--------|
| Blur | ⚡⚡⚡ | ⭐⭐ | Low |
| Box Blur | ⚡⚡⚡ | ⭐⭐ | Low |
| Gaussian Blur | ⚡⚡ | ⭐⭐⭐ | Low |
| Cartoonize | ⚡ | ⭐⭐⭐⭐ | Medium |
| Custom Kernel | ⚡⚡ | Variable | Low |

---

## 🔍 Troubleshooting

### Common Issues

**Issue**: "ModuleNotFoundError: No module named 'cv2'"
```bash
Solution: pip install opencv-python
```

**Issue**: "FileNotFoundError: Image not found"
```python
Solution: Use absolute path or verify file location
image = cv2.imread(r'C:\path\to\image.jpg')
```

**Issue**: Image appears corrupted after filtering
```python
Solution: Ensure proper data type
filtered = cv2.filter2D(img, cv2.CV_32F, kernel)
```

---

## 💡 Tips & Best Practices

1. **Always verify input path** before running filters
2. **Use absolute paths** for reliable file access
3. **Test with small images first** before batch processing
4. **Backup original images** before applying filters
5. **Experiment with kernel sizes** for different effects
6. **Check image format** before processing (JPG, PNG, etc.)
7. **Use appropriate data types** (uint8 for standard images)

---

## 📈 Performance Optimization

### For Large Images:
```python
# Resize before processing
small = cv2.resize(image, (640, 480))
filtered = cv2.GaussianBlur(small, (5, 5), 0)
result = cv2.resize(filtered, image.shape[:2][::-1])
```

### For Real-time Processing:
```python
# Use smaller kernel sizes
blur = cv2.GaussianBlur(image, (3, 3), 0)  # Faster than (7,7)
```

---

## 🔗 Integration Examples

### With Web Applications (Flask)
```python
from flask import Flask, request, send_file
import cv2

app = Flask(__name__)

@app.route('/blur', methods=['POST'])
def blur_image():
    file = request.files['image']
    img = cv2.imread(file.filename)
    blurred = cv2.GaussianBlur(img, (5, 5), 0)
    cv2.imwrite('output.jpg', blurred)
    return send_file('output.jpg')
```

### With Data Processing Pipelines
```python
# Preprocessing for machine learning
img = cv2.imread('image.jpg')
gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)
blurred = cv2.GaussianBlur(gray, (5, 5), 0)
# Ready for ML model input
```

---

## 📚 References & Learning Resources

- OpenCV Official Documentation: https://docs.opencv.org/
- NumPy Array Operations: https://numpy.org/doc/
- Digital Image Processing Theory: https://en.wikipedia.org/wiki/Digital_image_processing
- Kernel Convolution: https://en.wikipedia.org/wiki/Kernel_(image_processing)

---

## 🚀 Future Enhancements

- [ ] GPU acceleration using CUDA
- [ ] Real-time video filter processing
- [ ] Web UI for interactive filter application
- [ ] Advanced color space filters (HSV, LAB)
- [ ] Machine learning-based filters
- [ ] Batch processing CLI tool
- [ ] Filter preview/comparison interface
- [ ] Custom filter builder utility
- [ ] Performance benchmarking tools
- [ ] Filter preset library

---

## 🤝 Contributing

Contributions welcome! To contribute:
1. Fork the repository
2. Create a feature branch (`git checkout -b feature/new-filter`)
3. Commit changes (`git commit -am 'Add new filter'`)
4. Push to branch (`git push origin feature/new-filter`)
5. Submit Pull Request

---

## 📄 License

This project is licensed under the included LICENSE file.

---

## 👤 Author

**Alihassan891u-lab**

---

## 💬 Support

For issues, questions, or suggestions, please create a GitHub issue or contact the repository maintainer.

---

## 🎨 Quick Start Examples

### Example 1: Apply Gaussian Blur
```bash
python Gaussian_Blur_An_Image.py
```
Then open your image file and save the blurred version.

### Example 2: Create Cartoon Effect
```bash
python Cartoonize_An_Image.py
```
Automatically applies bilateral filtering + edge detection.

### Example 3: Convert to Grayscale
```bash
python GrayScale_Filter_An_Image.py
```
Simple color to grayscale conversion.

---

**Happy Filtering!** 🎨✨

Last Updated: August 2026
