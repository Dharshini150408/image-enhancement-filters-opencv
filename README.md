# Image Smoothing and Sharpening Using OpenCV

## Aim

To write a Python program using OpenCV to apply different smoothing filters (Averaging, Weighted Averaging, Gaussian, Median) and sharpening filters (Laplacian Kernel and Laplacian Operator) for image enhancement, and display each result separately along with the original image for comparison.

---

## The program performs the following operations:

- Read and display an input image  
- Apply Averaging filter  
- Apply Weighted Averaging filter  
- Apply Gaussian filter  
- Apply Median filter  
- Apply Laplacian sharpening using kernel  
- Apply Laplacian operator  
- Display all outputs for comparison  

---

##  Software Used

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (cv2)  
- NumPy  
- Matplotlib  

---

##  Algorithm

### Step 1:
Import the required libraries: OpenCV, NumPy, and Matplotlib.

### Step 2:
Read the input image (e.g., `image.jpg`).

### Step 3:
Convert the image from BGR to RGB format for display.

### Step 4:
Apply Averaging Filter using `cv2.blur()`.

### Step 5:
Apply Weighted Averaging Filter using a custom kernel with `cv2.filter2D()`.

### Step 6:
Apply Gaussian Filter using `cv2.GaussianBlur()`.

### Step 7:
Apply Median Filter using `cv2.medianBlur()`.

### Step 8:
Apply Laplacian Sharpening using Kernel with `cv2.filter2D()`.

### Step 9:
Convert image to grayscale and apply Laplacian Operator using `cv2.Laplacian()`.

### Step 10:
Display all filtered images using a grid layout for comparison.

---

##  Developed By

- **Name:** DHARSHINI V 
- **Register No:** 212225100010

---
## Program
```

import cv2
import numpy as np
import matplotlib.pyplot as plt

# Step 1: Read the input image
img = cv2.imread("image.jpg")

if img is None:
    print("Error: Image not found!")
    exit()

# Step 2: Convert BGR to RGB
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

# Step 3: Averaging Filter
averaging = cv2.blur(img, (5, 5))

# Step 4: Weighted Averaging Filter
kernel = np.array([[1, 2, 1],
                   [2, 4, 2],
                   [1, 2, 1]], dtype=np.float32) / 16

weighted = cv2.filter2D(img, -1, kernel)

# Step 5: Gaussian Filter
gaussian = cv2.GaussianBlur(img, (5, 5), 0)

# Step 6: Median Filter
median = cv2.medianBlur(img, 5)

# Step 7: Laplacian Sharpening using Kernel
laplacian_kernel = np.array([[0, -1, 0],
                             [-1, 5, -1],
                             [0, -1, 0]])

laplacian_sharpen = cv2.filter2D(img, -1, laplacian_kernel)

# Step 8: Laplacian Operator
gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)

laplacian = cv2.Laplacian(gray, cv2.CV_64F)

laplacian = cv2.convertScaleAbs(laplacian)

# Step 9: Convert all outputs to RGB for display
images = [
    img_rgb,
    cv2.cvtColor(averaging, cv2.COLOR_BGR2RGB),
    cv2.cvtColor(weighted, cv2.COLOR_BGR2RGB),
    cv2.cvtColor(gaussian, cv2.COLOR_BGR2RGB),
    cv2.cvtColor(median, cv2.COLOR_BGR2RGB),
    cv2.cvtColor(laplacian_sharpen, cv2.COLOR_BGR2RGB),
    laplacian
]

titles = [
    "Original Image",
    "Averaging Filter",
    "Weighted Averaging",
    "Gaussian Filter",
    "Median Filter",
    "Laplacian Sharpening",
    "Laplacian Operator"
]

# Step 10: Display all images
plt.figure(figsize=(14, 10))

for i in range(7):
    plt.subplot(3, 3, i + 1)
    plt.imshow(images[i], cmap='gray' if i == 6 else None)
    plt.title(titles[i])
    plt.axis('off')

plt.tight_layout()
plt.show()
```
##  Output
### Smoothing Filters

- Averaging filter produces blurred image  
- Weighted averaging provides smoother result with less distortion  
- Gaussian filter preserves edges better while reducing noise  
- Median filter removes salt-and-pepper noise effectively  
<img width="1836" height="972" alt="image" src="https://github.com/user-attachments/assets/7b23446b-715e-4e3d-aa95-9ee2900dd8a0" />

###  Sharpening Filters

- Laplacian kernel enhances edges and fine details  
- Laplacian operator detects edges clearly in grayscale  
<img width="1907" height="985" alt="image" src="https://github.com/user-attachments/assets/73cc66ee-5e4e-4bf6-a2d0-d3589bf5e267" />

---

##  Result

Thus, smoothing filters and sharpening filters are successfully implemented using OpenCV.

The smoothing filters reduce noise and improve image quality, while sharpening filters enhance edges and details for better feature extraction.
