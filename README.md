# NAME: SANJAI U
# REG.NO: 212224240145
# Sturdy-Octo-Disco-Adding-Sunglasses-for-a-Cool-New-Look

Sturdy Octo Disco is a fun project that adds sunglasses to photos using image processing.

Welcome to Sturdy Octo Disco, a fun and creative project designed to overlay sunglasses on individual passport photos! This repository demonstrates how to use image processing techniques to create a playful transformation, making ordinary photos look extraordinary. Whether you're a beginner exploring computer vision or just looking for a quirky project to try, this is for you!

## Features:
- Detects the face in an image.
- Places a stylish sunglass overlay perfectly on the face.
- Works seamlessly with individual passport-size photos.
- Customizable for different sunglasses styles or photo types.

## Technologies Used:
- Python
- OpenCV for image processing
- Numpy for array manipulations

## How to Use:
1. Clone this repository.
2. Add your passport-sized photo to the `images` folder.
3. Run the script to see your "cool" transformation!

## Applications:
- Learning basic image processing techniques.
- Adding flair to your photos for fun.
- Practicing computer vision workflows.

## program
```
import cv2
import numpy as np
import matplotlib.pyplot as plt


faceImage = cv2.imread('ws.jpg')
plt.imshow(faceImage[:,:,::-1]);plt.title("Face")


faceImage.shape

glassPNG = cv2.imread('sunglass.png',-1)
plt.imshow(glassPNG[:,:,::-1]);plt.title("glassPNG")


glassPNG = cv2.resize(glassPNG,(500,400))
print("image Dimension ={}".format(glassPNG.shape))


glassBGR = glassPNG[:,:,0:3]
glassMask1 = glassPNG[:,:,3]


plt.figure(figsize=[15,15])
plt.subplot(121);plt.imshow(glassBGR[:,:,::-1]);plt.title('Sunglass Color channels');
plt.subplot(122);plt.imshow(glassMask1,cmap='gray');plt.title('Sunglass Alpha channel');


faceWithGlassesNaive = faceImage.copy()

faceWithGlassesNaive[230:630,250:750]=glassBGR

plt.imshow(faceWithGlassesNaive[...,::-1])


glassMask = cv2.merge((glassMask1,glassMask1,glassMask1))

glassMask = np.uint8(glassMask/255)

faceWithGlassesArithmetic = faceImage.copy()

eyeROI= faceWithGlassesArithmetic[230:630,250:750]

maskedEye = cv2.multiply(eyeROI,(1-  glassMask ))

maskedGlass = cv2.multiply(glassBGR,glassMask)

eyeRoiFinal = cv2.add(maskedEye, maskedGlass)

plt.figure(figsize=[20,20])
plt.subplot(131);plt.imshow(maskedEye[...,::-1]);plt.title("Masked Eye Region")
plt.subplot(132);plt.imshow(maskedGlass[...,::-1]);plt.title("Masked Sunglass Region")
plt.subplot(133);plt.imshow(eyeRoiFinal[...,::-1]);plt.title("Augmented Eye and Sunglass")


faceWithGlassesArithmetic[230:630,250:750]=eyeRoiFinal

plt.figure(figsize=[20,20]);
plt.subplot(121);plt.imshow(faceImage[:,:,::-1]); plt.title("Original Image");
plt.subplot(122);plt.imshow(faceWithGlassesArithmetic[:,:,::-1]);plt.title("With Sunglasses");

```
## output:
<img width="542" height="581" alt="image" src="https://github.com/user-attachments/assets/164b946d-6032-489d-8dfa-2d8af2c72751" />

<img width="892" height="392" alt="image" src="https://github.com/user-attachments/assets/ff89c148-9d73-4c69-83ea-bcd32564852b" />

<img width="1397" height="250" alt="image" src="https://github.com/user-attachments/assets/21ed5329-19cf-4168-aa9d-731cbb2898d1" />

<img width="568" height="562" alt="image" src="https://github.com/user-attachments/assets/8b3494bd-03b6-4081-9b02-515c326f5eb7" />

<img width="1461" height="180" alt="image" src="https://github.com/user-attachments/assets/c3c3cd28-552c-4255-841c-9789c15a9bfb" />

<img width="1037" height="660" alt="image" src="https://github.com/user-attachments/assets/8b78efe8-03d0-4fb9-84d6-4dd0119acb22" />

Feel free to fork, contribute, or customize this project for your creative needs!
