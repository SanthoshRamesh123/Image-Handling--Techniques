# Image-Handling--Techniques
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
- **Name:** SANTHOSH R  
- **Register Number:** 212224230249

  ### Ex. No. 01

#### 1. Read the image ('Eagle_in_Flight.jpg') using OpenCV imread() as a grayscale image.
```python
img_bgr  = cv2.imread("Eagle_in_Flight.jpg",0)
```

#### 2. Print the image width, height & Channel.
```python
img_bgr.shape
```

#### 3. Display the image using matplotlib imshow().
```python
plt.imshow(img_bgr,cmap = "gray")
```

#### 4. Save the image as a PNG file using OpenCV imwrite().
```python
cv2.imwrite("Eagle_gray.png",img_bgr)
```

#### 5. Read the saved image above as a color image using cv2.cvtColor().
```python
load_img = cv2.imread("Eagle_in_Flight.jpg")
load_rgb = cv2.cvtColor(load_img,cv2.COLOR_BGR2RGB)
plt.imshow(load_rgb)
```

#### 6. Display the Colour image using matplotlib imshow() & Print the image width, height & channel.
```python
plt.imshow(load_rgb)
```

#### 7. Crop the image to extract any specific (Eagle alone) object from the image.
```python
cropped_region = load_rgb[20:420,200:600]
plt.figure(figsize = [15,10])
plt.subplot(221)
plt.imshow(load_rgb)
plt.title("Original image")
plt.subplot(222)
plt.imshow(cropped_region)
plt.title("cropped image")
```

#### 8. Resize the image up by a factor of 2x.
```python
resized = cv2.resize(cropped_region,None,fx = 2,fy = 1)
plt.imshow(resized)
```

#### 9. Flip the cropped/resized image horizontally.
```python
flipped =  cv2.flip(resized,1)
plt.imshow(flipped)
```

#### 10. Read in the image ('Apollo-11-launch.jpg').
```python
image = cv2.imread('Apollo-11-launch.jpg')
```

#### 11. Add the following text to the dark area at the bottom of the image (centered on the image):
```python
text = 'Apollo 11 Saturn V Launch, July 16, 1969'
font_face = cv2.FONT_HERSHEY_PLAIN
withtext =  cv2.putText(image,text,(400,700),font_face,2,(255,0,0),5)
plt.imshow(image)
```

#### 12. Draw a magenta rectangle that encompasses the launch tower and the rocket.
```python
rect_img = cv2.rectangle(image,(400,100),(800,600),(0,255,0),5)
```

#### 13. Display the final annotated image.
```python
plt.imshow(rect_img)
```

#### 14. Read the image ('Boy.jpg').
```python
boy_image  = cv2.imread("boy.jpg")
```

#### 15. Adjust the brightness of the image.
```python
matrix_ones = np.ones(boy_image.shape,dtype='uint8') 
bright = matrix_ones*50
```

#### 16. Create brighter and darker images.
```python
img_brighter = cv2.add(boy_image, bright)
img_darker = cv2.subtract(boy_image, bright)
```

#### 17. Display the images (Original Image, Darker Image, Brighter Image).
```python
plt.figure(figsize=[20,10])
plt.subplot(131)
plt.imshow(img_brighter[:,:,::-1])
plt.title("Brighter")
plt.subplot(132)
plt.imshow(boy_image[:,:,::-1])
plt.title("Original")
plt.subplot(133)
plt.imshow(img_darker[:,:,::-1])
plt.title("Darker")
```

#### 18. Modify the image contrast.
```python
matrix1 = np.ones(boy_image.shape, dtype=np.float64) * 1.1
matrix2 = np.ones(boy_image.shape, dtype=np.float64) * 1.2

matrix3 = np.ones(boy_image.shape, dtype=np.float64) * 0.1

img_float = boy_image.astype(np.float64)
img_higher1 = img_float * matrix1
img_higher2 = img_float * matrix2
img_lower1 = img_float * matrix3
```

#### 19. Display the images (Original, Lower Contrast, Higher Contrast).
```python
plt.figure(figsize=[20,10])
plt.subplot(131)
plt.imshow(img_higher2[:,:,::-1])
plt.title("Higher Contrast")
plt.subplot(132)
plt.imshow(boy_image[:,:,::-1])
plt.title("Original")
plt.subplot(133)
plt.imshow(img_lower1[:,:,::-1])
plt.title("Lower Contrast")
```

#### 20. Split the image (boy.jpg) into the B,G,R components & Display the channels.
```python
img2 = cv2.imread("boy.jpg")
B, G, R = cv2.split(img2)
plt.figure(figsize=[20,10])

plt.subplot(141)
plt.imshow(B)
plt.title("Blue")
plt.axis("off")

plt.subplot(142)
plt.imshow(G)
plt.title("Green")
plt.axis("off")

plt.subplot(143)
plt.imshow(R)
plt.title("Red")
plt.axis("off")

plt.subplot(144)
plt.imshow(img2[:,:,::-1])
plt.title("Original")
plt.axis("off")
```

#### 21. Merged the R, G, B , displays along with the original image
```python
merged_img2 = cv2.merge((B,G,R))
plt.figure(figsize = [20,10])

plt.subplot(121)
plt.imshow(merged_img2[:,:,::-1])
plt.title("merged image")
plt.axis("off")

plt.subplot(122)
plt.imshow(img2[:,:,::-1])
plt.title("orignal")
plt.axis("off")
```

#### 22. Split the image into the H, S, V components & Display the channels.
```python
hsv_img = cv2.cvtColor(img2, cv2.COLOR_BGR2HSV)
H, S, V = cv2.split(hsv_img)
plt.figure(figsize = [20,10])

plt.subplot(131)
plt.imshow(H)
plt.title("Hue")
plt.axis("off")

plt.subplot(132)
plt.imshow(S)
plt.title("Saturation")
plt.axis("off")

plt.subplot(133)
plt.imshow(V)
plt.title("Value")
plt.axis("off")
plt.show()
```
#### 23. Merged the H, S, V, displays along with original image.
```python
merged_img3 = cv2.merge((H,S,V))
plt.figure(figsize = [20,10])

final_image = cv2.cvtColor(merged_img3, cv2.COLOR_HSV2BGR)

plt.subplot(121)
plt.imshow(final_image[:,:,::-1])
plt.title("Merged image")
plt.axis("off")

plt.subplot(122)
plt.imshow(img2[:,:,::-1])
plt.title("Original image")
plt.axis("off")
```

## Output:
- **i)** Read and Display an Image.  
  <br><img width="666" height="459" alt="Screenshot 2026-04-27 103821" src="https://github.com/user-attachments/assets/3a7bba51-d5dc-4bb7-811d-17ba0e66c182" />
- **ii)** Adjust Image Brightness.  
  <br><img width="1284" height="382" alt="image" src="https://github.com/user-attachments/assets/13b4d759-c77c-4ec9-95a2-2b590faabbd9" />
- **iii)** Modify Image Contrast.  
  <br><img width="1268" height="313" alt="Screenshot 2026-04-27 104009" src="https://github.com/user-attachments/assets/a02a15bb-10e8-41c6-b671-93078afc79ac" />



## Result:
Thus, the images were read, displayed, brightness and contrast adjustments were made, and bitwise operations were performed successfully using the Python program.
