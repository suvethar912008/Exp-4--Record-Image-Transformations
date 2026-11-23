# Exp-4--Record-Image-Transformations
# Aim
To write a Python program using OpenCV to perform various geometric transformations on an image.

The program performs the following operations:

• Image Translation • Image Scaling (Resizing) • Image Shearing • Image Reflection (Flipping) • Image Rotation

# Software Used
• Anaconda – Python 3.7 • Jupyter Notebook / VS Code • OpenCV (cv2) • NumPy • Matplotlib • Algorithm

# Step 1:
Import the required libraries: OpenCV, NumPy, and Matplotlib.

# Step 2:
Read the input image in color mode.

# Step 3: Image Translation
Create a translation matrix to shift the image Move the image 50 pixels to the right and 80 pixels down Apply transformation using cv2.warpAffine() Display original and translated images

# Step 4: Image Scaling
Resize the image to 0.5× (downscale) Resize the image to 2× (upscale) Use cv2.resize() Display original, downscaled, and upscaled images

# Step 5: Image Shearing
Create transformation matrices for: Horizontal shearing Vertical shearing Apply transformations using cv2.warpAffine() Display original and sheared images

# Step 6: Image Reflection
Perform flipping using cv2.flip(): Horizontal reflection Vertical reflection Both axes Display all reflected images

# Step 7: Image Rotation
Create rotation matrices for: 45° rotation 90° rotation Use cv2.getRotationMatrix2D() and cv2.warpAffine() Display original and rotated images

# Program

Developed By: Name: Rasiga S

Register No: 212225220081

# Step 1 Original Image and Image Translation
```
import cv2
import numpy as np
import matplotlib.pyplot as plt

image = cv2.imread('pet.png') 

plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB)) 
plt.title("Original Image")  
plt.axis('off')
tx, ty = 100, 50 
M_translation = np.float32([[1, 0, tx], [0, 1, ty]])  
translated_image = cv2.warpAffine(image, M_translation, (image.shape[1], image.shape[0]))  
plt.imshow(cv2.cvtColor(translated_image, cv2.COLOR_BGR2RGB))  # Display the translated image
plt.title("Translated Image")  
plt.axis('off')
```
# Step 2: Image Scaling
```
fx, fy = 5.0, 2.0  
scaled_image = cv2.resize(image, None, fx=fx, fy=fy, interpolation=cv2.INTER_LINEAR)
plt.imshow(cv2.cvtColor(scaled_image, cv2.COLOR_BGR2RGB))  # Display the scaled image
plt.title("Scaled Image")  # Set title
plt.axis('off')
```
# Step 3: Image Shearing
```
shear_matrix = np.float32([[1, 0.5, 0], [0.5, 1, 0]])  # Shearing matrix
sheared_image = cv2.warpAffine(image, shear_matrix, (image.shape[1], image.shape[0]))
plt.imshow(cv2.cvtColor(sheared_image, cv2.COLOR_BGR2RGB))  # Display the sheared image
plt.title("Sheared Image")  # Set title
plt.axis('off')
```
# Step 4: Image Reflection
```
reflected_image = cv2.flip(image, 2)  # Flip the image horizontally (1 means horizontal flip)
plt.imshow(cv2.cvtColor(reflected_image, cv2.COLOR_BGR2RGB))  # Display the reflected image
plt.title("Reflected Image")  # Set title
plt.axis('off')

```
# Step 5: Image Rotation
```
(height, width) = image.shape[:2]  # Get the image height and width
angle = 45  # Rotation angle in degrees (rotate by 45 degrees)
center = (width // 2, height // 2)  # Set the center of rotation to the image center
M_rotation = cv2.getRotationMatrix2D(center, angle, 1)  # Get the rotation matrix
# getRotationMatrix2D: Takes the center of rotation, angle, and scale factor (1 means no scaling)
rotated_image = cv2.warpAffine(image, M_rotation, (width, height))  # Apply rotation
plt.imshow(cv2.cvtColor(rotated_image, cv2.COLOR_BGR2RGB))  # Display the rotated image
plt.title("Rotated Image")  # Set title
plt.axis('off')
```

# Step 6: Cropped Image
```
x, y, w, h = 100, 100, 200, 150  # Define the top-left corner (x, y) and the width (w) and height (h) of the crop
cropped_image = image[y:y+h, x:x+w]
plt.imshow(cv2.cvtColor(cropped_image, cv2.COLOR_BGR2RGB))  # Display the cropped image
plt.title("Cropped Image")  # Set title
plt.axis('off')
```

# Output

# Image Translation
• Original image is displayed

• Translated image (shifted right and down) is displayed

<img width="647" height="392" alt="image" src="https://github.com/user-attachments/assets/b1c3b727-4349-4b21-af9d-7bcdfccc39c5" />

<img width="660" height="381" alt="image" src="https://github.com/user-attachments/assets/ab426e55-18e8-4fa0-921f-603776b2efe6" />


# Image Scaling
Original image is displayed

Downscaled image (0.5×) is displayed

Upscaled image (2×) is displayed


<img width="677" height="197" alt="image" src="https://github.com/user-attachments/assets/f51a8357-e750-4d9a-a2ac-575ad26a1809" />


# Image Shearing
Original image is displayed Horizontally sheared image is displayed Vertically sheared image is displayed image image

<img width="667" height="387" alt="image" src="https://github.com/user-attachments/assets/d2b9f638-fe6b-48cc-97b8-236ed4308ce4" />


# Image Reflection
Original image is displayed

Horizontally flipped image is displayed

Vertically flipped image is displayed

Both-axis flipped image is displayed


<img width="652" height="390" alt="image" src="https://github.com/user-attachments/assets/84008d88-35ba-48f7-9866-3b62357db228" />


# Image Rotation
Original image is displayed

45° rotated image is displayed

90° rotated image is displayed

<img width="667" height="371" alt="image" src="https://github.com/user-attachments/assets/13044c88-6462-4512-a127-5351194104ba" />

# Result
Thus, various geometric transformations such as translation, scaling, shearing, reflection, and rotation are successfully performed using OpenCV. These transformations demonstrate how images can be spatially manipulated for different computer vision applications.
