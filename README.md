# Lane Detection
## Aim
To implement a basic lane detection pipeline using OpenCV by completing missing code segments at specified locations.

## Learning Objective
1.Understand each stage of image processing
2.Learn how to build a complete computer vision pipeline
3.Practice writing code in guided sections
#### Important Instruction: 👉 Write code ONLY in places marked as # Your Code Here 👉 Do NOT modify any other part of the code

## Software Used
1.Anaconda – Python 3.7
2.Jupyter Notebook / VS Code
3.OpenCV (cv2)
4.NumPy
5.Matplotlib

## PROGRAMM & OUTPUT:
```python
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Step 2: Load the image using imread() from cv2 module
image = cv2.imread('lane.jpg')  # Replace 'image.jpg' with your image path

# Step 3: Convert the image to grayscale
gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

# Input image and grayscale image
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))  # Convert image to RGB for displaying
plt.title("Input Image")
plt.axis('off')
```
<img width="698" height="271" alt="image" src="https://github.com/user-attachments/assets/6f0d2eae-b98c-47df-9798-236a1c807b31" />

```python
plt.imshow(gray_image, cmap='gray')
plt.title("Grayscale Image")
plt.axis('off')
```
<img width="673" height="271" alt="image" src="https://github.com/user-attachments/assets/41f5d237-fb49-4561-aedd-44aae704bece" />

```python
# Step 4: Using Canny operator from cv2, detect the edges of the image
edges = cv2.Canny(gray_image, 50, 150)  # Canny edge detection with threshold values 50 and 150

# Canny Edge Detector output
plt.imshow(edges, cmap='gray')
plt.title("Canny Edge Detector")
plt.axis('off')
```
<img width="687" height="263" alt="image" src="https://github.com/user-attachments/assets/093154f0-fe3b-4d13-8742-faf75d76099d" />

```python
# Step 5: Detect line coordinates using HoughLinesP()
lines = cv2.HoughLinesP(
    edges,
    1,
    np.pi / 180,
    100,
    minLineLength=50,
    maxLineGap=10
)

# Step 6: Draw the detected lines on the original image
if lines is not None:
    for line in lines:
        if len(line.shape) == 2:
            x1, y1, x2, y2 = line[0]
        else:
            x1, y1, x2, y2 = line

        cv2.line(image, (x1, y1), (x2, y2), (0, 255, 0), 2)

# Display the result
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title("Result of Hough Transform")
plt.axis('off')
plt.show()
```
<img width="665" height="247" alt="image" src="https://github.com/user-attachments/assets/4fb26729-79a7-4976-85b3-b22769e2cabd" />

## Result:
Thus, the lane detection pipeline is successfully implemented by completing the missing code sections. The system detects and highlights lane lines effectively.
