# Localization


```python
from localization import geolocalization
import rasterio as rio
from rasterio.plot import show
import cv2 as cv
import matplotlib.pyplot as plt
import numpy as np
```

#### Read the orthophoto / georeferenced image


```python
train = rio.open(r'Examples/train.tif')
show(train)
```


![png](output_2_0.png)



#### Read the non georeferenced image


```python
query = rio.open(r'Examples/query.jpg')
show(query)
```


![png](output_4_0.png)



The ```geolocalization``` will detects where's the non georeferenced image in the orthophoto

<!-- 
```python
fig, (ax1, ax2) = plt.subplots(1, 2,figsize=(15,10))
ax1.set_title('orthophoto / georeferenced image',fontsize=16,pad=10)
ax1.imshow(train.read(1))
ax1.set_axis_off()
ax2.set_title('non georeferenced image',fontsize=16,pad=10)
ax2.imshow(query.read(1))
ax2.set_axis_off()
``` -->


![png](output_6_0.png)


#### Initialize the ```geolocalization```


```python
glocal = geolocalization(train,query)
```

#### detection where's the non georeferenced image in the orthophoto then georeferencing it


```python
glocal.georeference(1,0.4)
```
    Georeferencing done successfully... elapsed time\ 0.191 m
    





```python
glocal.solve(1,0.4)
```




    ((91041.68140458249, 94815.2122869065),
     (91041.68396886346, 94488.56103586656),
     (91435.03672220978, 94488.55975372608),
     (91435.03031150733, 94815.21119708709))






The ```geolocalization``` detected where's the non georeferenced image in the orthophoto

<!-- 
```python
fig, (ax1, ax2) = plt.subplots(1, 2,figsize=(15,10))
ax1.set_title('orthophoto / georeferenced image',fontsize=16,pad=10)
ax1.imshow(img2)
ax1.set_axis_off()
ax2.set_title("geolocalization's result",fontsize=16,pad=10)
ax2.imshow(query.read(1))
ax2.set_axis_off()
``` -->


![png](output_16_0.png)



```python
## Yasser I Barhoom
```
