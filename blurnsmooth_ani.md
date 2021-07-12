### 1. Averaging

**Averaging** method is implemented by convolving the image with a normalized box filter. It takes the average of all the pixels under the kernel area and places the average at the place of central element. The kernel i.e. the box filter looks something like this:

![](images\averagefilter.jpg)

where kwidth and kheight are 2d dimensions of kernel.

Averaging can be implemented using some of the useful *OpenCV* functions like **cv2.blur()** or **cv2.boxFilter()**.

Syntax of cv2.blur() is 

```python
blur = cv2.blur(src, ksize, dst, anchor = (-1,-1), borderType)
```

where 

> **src** = image that is to be blurred
>
> **ksize** = A tuple with height and width of kernel
>
> **dst** = output image with same size and type as the source image
>
> **anchor** = integer type variable representing anchor point, has value (-1, -1) as its default value meaning anchor is at the kernel center.
>
> **borderType** = An optional argument to decide what kind of border needs to be added and is defined by flags like cv2.BORDER_CONSTANT, cv2.BORDER_REFLECT, etc.
>
> **returns** a blurred image of same size and type as source image

Let's try this on an example image

<img src="images\download.png" alt="download" style="zoom: 80%;" />

```python
import cv2

image = cv2.imread('devincept.jpg')
# ksize
ksize = (8, 8)  
# Using cv2.blur() method 
image = cv2.blur(image, ksize) 
cv2.imshow(image)
```

Output:

<img src="images\download (3).png" alt="download (1)" style="zoom: 80%;" />

if we increase our size of kernel, our image gets more blurry. lets try `ksize=(15,15)`, we get the image like 

<img src="images\download (2).png" alt="download (2)" style="zoom: 80%;" />

### Gaussian Blurring

In Gaussian Blurring we use a Gaussian kernel instead of using a box filter.It can be implemented using the method **cv2.GaussianBlur()**. Gaussian blurring is very successful in removing Gaussian noise from an image.

Syntax of cv2.GaussianBlur() is

```python
blur = cv.GaussianBlur(src,dst,ksize,sigmaX)
```



where

> **src** = image that is to be blurred
>
> **ksize** = A tuple with height and width of kernel. Note that the kernel width and height 	should be an odd number.
>
> **dst** = output image with same size and type as the source image
>
> **sigmaX** = a double type variable which is used for the Gaussian kernel standard deviation in X direction.

Lets try this on our previous example

```python
blur = cv2.GaussianBlur(image,(9,9),0)
cv2.imshow(blur)
```

<img src="images\download (4).png" alt="download (4)" style="zoom: 80%;" />
