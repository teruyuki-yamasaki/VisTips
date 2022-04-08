# VisTips
Tips for Data Visualisation


## Images
### rgb arrays to gif
```
import PIL 
from io import BytesIO 
from IPython.display import Image, display, clear_output

def show(rgb_arrays, fmt='png'):
    for i in range(rgb_arrays.shape[0]):
        f = BytesIO()
        rgb = rgb_arrays[i] 
        PIL.Image.fromarray(rgb).save(f, fmt)
        display(Image(data=f.getvalue()))
        clear_output(wait=True)

def save(rgb_arrays, path='./array.gif'):
    im = [PIL.Image.fromarray(rgb) for rgb in rgb_arrays]
    im[0].save(path, save_all=True, append_images=im[1:], duration=50, loop=0)

n = 500; h = 256; w = 256
random_rgb_arrays = np.random.randint(0, 255, n*h*w*3).reshape(n,h,w,3).astype(np.uint8)
show(random_rgb_arrays)
save(random_rgb_arrays)
```
