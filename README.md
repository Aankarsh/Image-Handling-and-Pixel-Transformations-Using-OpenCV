# Image-Handling-and-Pixel-Transformations-Using-OpenCV 

## AIM:
Write a Python program using OpenCV that performs the following tasks:

1) Read and Display an Image.  
2) Adjust the brightness of an image.  
3) Modify the image contrast.  
4) Generate a third image using bitwise operations.

## Software Required:
- Anaconda - Python 3.7
- Jupyter Notebook (for interactive development and execution)

## Algorithm:

### Step 1:
Load an image from your local directory and display it.
```
img_gray = cv2.imread('flying_eagle.jpg', cv2.IMREAD_GRAYSCALE)
```

### Step 2:
Create a matrix of ones (with data type float64) to adjust brightness.

### Step 3:
Create brighter and darker images by adding and subtracting the matrix from the original image.  
Display the original, brighter, and darker images.

### Step 4:
Modify the image contrast by creating two higher contrast images using scaling factors of 1.1 and 1.2 (without overflow fix).  
Display the original, lower contrast, and higher contrast images.

### Step 5:
Split the image (boy.jpg) into B, G, R components and display the channels

## Program Developed By:
- **Name:** AANKARSH J.
- **Register Number:** 212223233001

  ### Ex. No. 01

#### 1. Read the image ('flying_eagle.jpg') using OpenCV imread() as a grayscale image.
```python
import cv2
import numpy as np
import matplotlib.pyplot as plt
img_gray = cv2.imread('flying_eagle.jpg', cv2.IMREAD_GRAYSCALE)
```

#### 2. Print the image width, height & Channel.
```python
print("Grayscale Image Shape:", img_gray.shape)
```

#### 3. Display the image using matplotlib imshow().
```python
plt.imshow(img_gray, cmap='gray')
plt.title("Grayscale Eagle")
plt.axis("off")
plt.show()
```

#### 4. Save the image as a PNG file using OpenCV imwrite().
```python
cv2.imwrite("flying_eagle.png", img_gray)
```

#### 5. Read the saved image above as a color image using cv2.cvtColor().
```python
img_color = cv2.imread("flying_eagle.png")
img_color = cv2.cvtColor(img_color, cv2.COLOR_BGR2RGB)
```

#### 6. Display the Colour image using matplotlib imshow() & Print the image width, height & channel.
```python
plt.imshow(img_color)
plt.title("Color Image")
plt.axis("off")
plt.show()
print("Color Image Shape:", img_color.shape) 
```

#### 7. Crop the image to extract any specific (Eagle alone) object from the image.
```python
cropped = img_color[100:400, 150:500]  
plt.imshow(cropped)
plt.title("Cropped Eagle")
plt.axis("off")
plt.show()
```

#### 8. Resize the image up by a factor of 2x.
```python
resized = cv2.resize(cropped, None, fx=2, fy=2)
plt.imshow(resized)
plt.title("Resized Eagle (2x)")
plt.axis("off")
plt.show()
```

#### 9. Flip the cropped/resized image horizontally.
```python
flipped = cv2.flip(resized, 1)
plt.imshow(flipped)
plt.title("Flipped Image")
plt.axis("off")
plt.show()
```

#### 10. Read in the image ('chandrayan.jpg').
```python
chand = cv2.imread('chandrayan.jpg')
chand = cv2.cvtColor(chand, cv2.COLOR_BGR2RGB)
```

#### 11. Add the following text to the dark area at the bottom of the image (centered on the image):
```python
text = "Chandrayan Launch"
font_face = cv2.FONT_HERSHEY_PLAIN
cv2.putText(chand, text, (100, 950), font_face, 2, (255,255,255), 2, cv2.LINE_AA)
```

#### 12. Draw a magenta rectangle that encompasses the launch tower and the rocket.
```python
rect_color = magenta
cv2.rectangle(chand, (250,200), (600,950), (255,0,255), 3)
```

#### 13. Display the final annotated image.
```python
plt.imshow(chand)
plt.title("Chandrayan Annotated")
plt.axis("off")
plt.show()

```

#### 14. Read the image ('Boy.jpg').
```python
boy = cv2.imread("Boy.jpg")
boy = cv2.cvtColor(boy, cv2.COLOR_BGR2RGB)
```

#### 15. Adjust the brightness of the image.
```python
# Create a matrix of ones (with data type float64)
matrix = np.ones(boy.shape, dtype="uint8") * 50
```

#### 16. Create brighter and darker images.
```python
img_brighter = cv2.add(boy, matrix)
img_darker = cv2.subtract(boy, matrix)
```

#### 17. Display the images (Original Image, Darker Image, Brighter Image).
```python
fig, ax = plt.subplots(1,3, figsize=(12,5))
ax[0].imshow(boy); ax[0].set_title("Original")
ax[1].imshow(img_darker); ax[1].set_title("Darker")
ax[2].imshow(img_brighter); ax[2].set_title("Brighter")
for a in ax: a.axis("off")
plt.show()

```

#### 18. Modify the image contrast.
```python
# Create two higher contrast images using the 'scale' option with factors of 1.1 and 1.2 (without overflow fix)
img_higher1 = cv2.convertScaleAbs(boy, alpha=1.1, beta=0)
img_higher2 = cv2.convertScaleAbs(boy, alpha=1.2, beta=0)
```

#### 19. Display the images (Original, Lower Contrast, Higher Contrast).
```python
fig, ax = plt.subplots(1,3, figsize=(12,5))
ax[0].imshow(boy); ax[0].set_title("Original")
ax[1].imshow(img_higher1); ax[1].set_title("Contrast x1.1")
ax[2].imshow(img_higher2); ax[2].set_title("Contrast x1.2")
for a in ax: a.axis("off")
plt.show()
```

#### 20. Split the image (boy.jpg) into the B,G,R components & Display the channels.
```python
b, g, r = cv2.split(boy)
fig, ax = plt.subplots(1,3, figsize=(12,5))
ax[0].imshow(b, cmap='gray'); ax[0].set_title("Blue Channel")
ax[1].imshow(g, cmap='gray'); ax[1].set_title("Green Channel")
ax[2].imshow(r, cmap='gray'); ax[2].set_title("Red Channel")
for a in ax: a.axis("off")
plt.show()
```

#### 21. Merged the R, G, B , displays along with the original image
```python
merged = cv2.merge([r,g,b])  
plt.imshow(merged)
plt.title("Merged Image (R,G,B)")
plt.axis("off")
plt.show()
```

#### 22. Split the image into the H, S, V components & Display the channels.
```python
hsv = cv2.cvtColor(boy, cv2.COLOR_RGB2HSV)
h, s, v = cv2.split(hsv)
fig, ax = plt.subplots(1,3, figsize=(12,5))
ax[0].imshow(h, cmap='gray'); ax[0].set_title("Hue")
ax[1].imshow(s, cmap='gray'); ax[1].set_title("Saturation")
ax[2].imshow(v, cmap='gray'); ax[2].set_title("Value")
for a in ax: a.axis("off")
plt.show()

```
#### 23. Merged the H, S, V, displays along with original image.
```
pythonmerged_hsv = cv2.merge([h,s,v])
plt.imshow(cv2.cvtColor(merged_hsv, cv2.COLOR_HSV2RGB))
plt.title("Merged HSV -> RGB")
plt.axis("off")
plt.show()
```

## Output:
- **i)** Read and Display an Image.
  1.Read 'Eagle_in_Flight.jpg' as grayscale and display:
 
![flying_eagle](https://github.com/user-attachments/assets/0e8d7f58-6252-4320-8246-f85ae222cbd9)


 2.Save image as PNG and display:
 <img width="515" height="319" alt="colour image" src="https://github.com/user-attachments/assets/c9244fc7-169c-4927-bf7a-7f9b9e052ffc" />



 3.Cropped image:
  <img width="472" height="409" alt="cropped" src="https://github.com/user-attachments/assets/6faac90e-5572-4b7c-b8ec-a16347bc068e" />

4.Resize and flip Horizontally:

 <img width="472" height="409" alt="image" src="https://github.com/user-attachments/assets/a0007b17-0ce5-43d7-8c11-6e14ae852d52" />


5.Read 'chandrayan.jpg' and Display the final annotated image:

<img width="515" height="365" alt="chandrayan" src="https://github.com/user-attachments/assets/2fb77d0c-d06e-46f1-92be-20085056725e" />


- **ii)** Adjust Image Brightness.
  
 1 .Create brighter and darker images and display:
 
<img width="950" height="222" alt="org_drk" src="https://github.com/user-attachments/assets/f3545362-763d-467c-bd4a-e609d72abc7c" />

- **iii)** Modify Image Contrast.
  Modify contrast using scaling factors 1.1 and 1.2:
  
<img width="950" height="222" alt="contrast img" src="https://github.com/user-attachments/assets/0dbf6e9b-b399-4c6e-8558-53023a9ff8e8" />

- **iv)** Generate Third Image Using Bitwise Operations.
1.Split 'Boy.jpg' into B, G, R components and display:
  
<img width="1337" height="340" alt="image" src="https://github.com/user-attachments/assets/310c7da5-f377-4ca2-be88-5a438c2317f7" />
  
2.Merge the R, G, B channels and display:

<img width="742" height="585" alt="image" src="https://github.com/user-attachments/assets/d8aecfd9-4065-4dc1-94c2-d3ee4edf69b4" />

3.Split the image into H, S, V components and display:

<img width="1352" height="348" alt="image" src="https://github.com/user-attachments/assets/173eac26-1243-4083-8916-d48406a8007b" />

4.Merge the H, S, V channels and display:

<img width="715" height="590" alt="image" src="https://github.com/user-attachments/assets/e3490875-761f-48b2-a72c-772b1bdcebef" />

## Result:
Thus, the images were read, displayed, brightness and contrast adjustments were made, and bitwise operations were performed successfully using the Python program.

