# THRESHOLDING
## Aim
To segment the image using global thresholding, adaptive thresholding and Otsu's thresholding using python and OpenCV.

## Software Required
Anaconda - Python 3.7
OpenCV

## Algorithm
### Step1: 
Load the necessary packages

### Step2: 
Read the Image and convert to grayscale

### Step3: 
Use Global thresholding to segment the image

### Step4: 
Use Adaptive thresholding to segment the image

### Step5: 
Use Otsu's method to segment the image and display results.

## Program
```
import cv2
import numpy as np
import matplotlib.pyplot as plt
```
#Read the Image and convert to grayscale
```
image = cv2.imread("dipt_img.jpg")  # Read the image using imread
image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)  # Convert the color from BGR to RGB
image_gray = cv2.imread("dipt_img.jpg", 0)  # Grayscale image
```
#Use Global thresholding to segment the image
```
ret, thresh_dipt1 = cv2.threshold(image_gray, 86, 255, cv2.THRESH_BINARY)
ret, thresh_dipt2 = cv2.threshold(image_gray, 86, 255, cv2.THRESH_BINARY_INV)
ret, thresh_dipt3 = cv2.threshold(image_gray, 86, 255, cv2.THRESH_TOZERO)
ret, thresh_dipt4 = cv2.threshold(image_gray, 86, 255, cv2.THRESH_TOZERO_INV)
ret, thresh_dipt5 = cv2.threshold(image_gray, 100, 255, cv2.THRESH_TRUNC)
```
#Use Otsu's method to segment the image
```
ret, thresh_dipt6 = cv2.threshold(image_gray, 0, 255, cv2.THRESH_BINARY + cv2.THRESH_OTSU)
```
#Use Adaptive thresholding to segment the image
```
thresh_dipt7 = cv2.adaptiveThreshold(image_gray, 255, cv2.ADAPTIVE_THRESH_MEAN_C, cv2.THRESH_BINARY, 11, 2)
thresh_dipt8 = cv2.adaptiveThreshold(image_gray, 255, cv2.ADAPTIVE_THRESH_GAUSSIAN_C, cv2.THRESH_BINARY, 11, 2)
```

#Display the results
```
titles = ["Gray Image", "Threshold Image (Binary)", "Threshold Image (Binary Inverse)", "Threshold Image (To Zero)",
          "Threshold Image (To Zero-Inverse)", "Threshold Image (Truncate)", "Otsu", "Adaptive Threshold (Mean)",
          "Adaptive Threshold (Gaussian)"]

images = [image_gray, thresh_dipt1, thresh_dipt2, thresh_dipt3, thresh_dipt4, thresh_dipt5, thresh_dipt6, thresh_dipt7, thresh_dipt8]

for i in range(0, 9):
    plt.figure(figsize=(10, 10))
    plt.subplot(1, 2, 1)
    plt.title("Original Image")
    plt.imshow(image_rgb)
    plt.axis("off")
    plt.subplot(1, 2, 2)
    plt.title(titles[i])
    if i == 0:
        plt.imshow(images[i], cmap='gray')  # Display grayscale image
    else:
        plt.imshow(images[i], cmap='gray')  # Display thresholded images
    plt.axis("off")
    plt.show()
```

## Output

### Original Image

<br>

![image](https://github.com/user-attachments/assets/eb7e3530-3534-4729-bb37-c55e5636baa3)


### Global Thresholding

<br>

![image](https://github.com/user-attachments/assets/4cc150ba-f918-4fc5-9ea2-787b08b73687)

<br>

![image](https://github.com/user-attachments/assets/8210145e-3c88-4629-a620-8f81e21be04c)

<br>

<br>

![image](https://github.com/user-attachments/assets/9ff10537-5d23-4bec-8d42-9456fb0f1b0d)

<br>

![image](https://github.com/user-attachments/assets/f2a6d7d3-70f7-490f-a5c0-ddb3d72d67a2)


### Adaptive Thresholding

<br>

![image](https://github.com/user-attachments/assets/489d9203-c016-4976-8861-09b11beef2b0)
<br>

![image](https://github.com/user-attachments/assets/c1726f6e-157c-4fe1-b1b5-0978c446bbd1)



### Optimum Global Thesholding using Otsu's Method

<br>

![image](https://github.com/user-attachments/assets/032859be-ca7f-42b9-89d0-e60d80995347)




## Result
Thus the images are segmented using global thresholding, adaptive thresholding and optimum global thresholding using python and OpenCV.
