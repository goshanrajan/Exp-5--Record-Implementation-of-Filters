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

- **Name:** T.Goshanrajan
- **Register No:** 212225040098 

---
```
# Import required libraries
import cv2
import numpy as np
import matplotlib.pyplot as plt
# Step 1: Read the input image
img = cv2.imread("colourful.jpg")

# Check whether image is loaded
if img is None:
    print("Error: Image not found.")
    exit()
# Step 2: Convert BGR to RGB for displaying
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
# ---------------------------------------------------
# Smoothing Filters
# ---------------------------------------------------

# 1. Averaging Filter
average = cv2.blur(img_rgb, (5, 5))

# 2. Weighted Averaging Filter
kernel = np.array([[1, 2, 1],
                   [2, 4, 2],
                   [1, 2, 1]], dtype=np.float32)

kernel = kernel / kernel.sum()

weighted = cv2.filter2D(img_rgb, -1, kernel)

# 3. Gaussian Filter
gaussian = cv2.GaussianBlur(img_rgb, (5, 5), 0)

# 4. Median Filter
median = cv2.medianBlur(img_rgb, 5)

# ---------------------------------------------------
# Sharpening Filters
# ---------------------------------------------------

# 5. Laplacian Sharpening using Kernel
laplacian_kernel = np.array([[0, -1, 0],
                             [-1, 5, -1],
                             [0, -1, 0]])

laplacian_sharp = cv2.filter2D(img_rgb, -1, laplacian_kernel)

# 6. Laplacian Operator
gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)

laplacian_operator = cv2.Laplacian(gray, cv2.CV_64F)
laplacian_operator = np.uint8(np.absolute(laplacian_operator))
# ---------------------------------------------------
# Display Results
# ---------------------------------------------------

plt.figure(figsize=(14, 10))

plt.subplot(2, 4, 1)
plt.imshow(img_rgb)
plt.title("Original Image")
plt.axis("off")

plt.subplot(2, 4, 2)
plt.imshow(average)
plt.title("Averaging Filter")
plt.axis("off")

plt.subplot(2, 4, 3)
plt.imshow(weighted)
plt.title("Weighted Averaging")
plt.axis("off")

plt.subplot(2, 4, 4)
plt.imshow(gaussian)
plt.title("Gaussian Filter")
plt.axis("off")

plt.subplot(2, 4, 5)
plt.imshow(median)
plt.title("Median Filter")
plt.axis("off")

plt.subplot(2, 4, 6)
plt.imshow(laplacian_sharp)
plt.title("Laplacian Kernel")
plt.axis("off")

plt.subplot(2, 4, 7)
plt.imshow(laplacian_operator, cmap="gray")
plt.title("Laplacian Operator")
plt.axis("off")

plt.tight_layout()
plt.show()
```

##  Output

### Smoothing Filters

- Averaging filter produces blurred image  
- Weighted averaging provides smoother result with less distortion  
- Gaussian filter preserves edges better while reducing noise  
- Median filter removes salt-and-pepper noise effectively  

###  Sharpening Filters

- Laplacian kernel enhances edges and fine details  
- Laplacian operator detects edges clearly in grayscale  

---
<img width="1390" height="706" alt="image" src="https://github.com/user-attachments/assets/abce8f96-97ff-41e7-a7b4-d3fa6bf76cd8" />

##  Result

Thus, smoothing filters and sharpening filters are successfully implemented using OpenCV.

The smoothing filters reduce noise and improve image quality, while sharpening filters enhance edges and details for better feature extraction.
