

``` python
import numpy as np
from scipy.linalg import svd
from PIL import Image
import mathplotlib.pyplot as plt

image = Image.open("image.bmp")
gray_image = image.convert("L")

plt.imshow(gray_image, cmap='gray')
plt.axis('off')
plt.title('Obraz w skali szarości')
plt.show()

gray_matrix = np.array(gray_image)
U, Σ, VT = svd(gray_matrix)

r = 10
mat = np.matrix(U[:, :r]) * np.diag(Σ[:r]) * np.matrix(VT[:r, :])

plt.imshow(mat, cmap='gray')
plt.axis('off')
plt.title('Obraz po kompresji')
plt.show()
```

