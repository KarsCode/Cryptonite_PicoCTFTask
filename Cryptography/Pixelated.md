### Pixelated

We are provided two images and are required to add their corresponding pixels in a form of superposition to obtain the resultant image and flag. So, when the two component images are superimposed, the original image appears. However, without the other component, a component image reveals no information about the original image.

![scrambled1](https://github.com/KarsCode/Cryptonite_PicoCTFTask/assets/117924364/47d660f1-b984-4b7d-b55b-80298fb03ab1)



![scrambled2](https://github.com/KarsCode/Cryptonite_PicoCTFTask/assets/117924364/a8cad9b8-b0ce-4c06-97a5-b518285bef05)


Using the following script we obtain the image and the flag
```python
import numpy as np
from PIL import Image

# Open images
im1 = Image.open("scrambled1.png")
im2 = Image.open("scrambled2.png")

# Make into Numpy arrays
im1np = np.array(im1)
im2np = np.array(im2)

# Add images
result = im2np + im1np
# Convert back to PIL image and save
Image.fromarray(result).save('out.png')
```



![out](https://github.com/KarsCode/Cryptonite_PicoCTFTask/assets/117924364/7010b594-ca29-475c-9685-fb0247c7c715)
