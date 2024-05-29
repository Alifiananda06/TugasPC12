# TugasPC12

# Input
 ```shell
import matplotlib.pyplot as plt
from skimage.morphology import convex_hull_image
from skimage import data, img_as_float
from skimage.util import invert

# Load the original image
image = invert(data.horse())

# Compute the convex hull of the image
chull = convex_hull_image(image)

# Plot the original and transformed images
fig, axes = plt.subplots(1, 2, figsize=(8, 4))
ax = axes.ravel()

ax[0].set_title('Original picture')
ax[0].imshow(image, cmap=plt.cm.gray)
ax[0].set_axis_off()

ax[1].set_title('Transformed picture')
ax[1].imshow(chull, cmap=plt.cm.gray)
ax[1].set_axis_off()

plt.tight_layout()
plt.show()
 ```

# Output

![image](https://github.com/Alifiananda06/TugasPC12/assets/115884834/0b3204cc-81fc-4eab-b5d1-c8f0aa6e40c7)

# Input

```shell
import matplotlib.pyplot as plt
from skimage.morphology import skeletonize
from skimage import data
from skimage.util import invert

# Invert the horse image
image = invert(data.horse())

# Perform skeletonization
skeleton = skeletonize(image)

# Display results
fig, axes = plt.subplots(nrows=1, ncols=2, figsize=(8, 4), sharex=True, sharey=True)
ax = axes.ravel()

ax[0].imshow(image, cmap=plt.cm.gray)
ax[0].axis('off')
ax[0].set_title('Original', fontsize=20)

ax[1].imshow(skeleton, cmap=plt.cm.gray)
ax[1].axis('off')
ax[1].set_title('Skeleton', fontsize=20)

fig.tight_layout()
plt.show()
```

# Output

![image](https://github.com/Alifiananda06/TugasPC12/assets/115884834/3b637b28-dc0b-4351-a82c-839dbb182fc5)

# Input

```shell
import numpy as np
import matplotlib.pyplot as plt
from skimage.color import rgb2gray
from skimage import data
from skimage.filters import gaussian
from skimage.segmentation import active_contour

# Load the astronaut image
img = data.astronaut()
img_gray = rgb2gray(img)

# Data for circular boundary
s = np.linspace(0, 2 * np.pi, 400)
x = 220 + 100 * np.cos(s)
y = 100 + 100 * np.sin(s)
init = np.array([x, y]).T

# Formation of the active contour
cntr = active_contour(gaussian(img_gray, 3), init, alpha=0.015, beta=10, gamma=0.001)

# Plotting the results
fig, ax = plt.subplots(1, 2, figsize=(7, 7))

ax[0].imshow(img_gray, cmap=plt.cm.gray)
ax[0].set_title("Original Image")

ax[1].imshow(img_gray, cmap=plt.cm.gray)
ax[1].plot(init[:, 0], init[:, 1], '--r', lw=3)  # Circular boundary
ax[1].plot(cntr[:, 0], cntr[:, 1], 'b', lw=3)    # Active contour
ax[1].set_title("Active Contour Image")

plt.tight_layout()
plt.show()
```

# Output

![image](https://github.com/Alifiananda06/TugasPC12/assets/115884834/d4b5203d-fb60-44cd-8246-3a06695573b8)
