# Geo-Localization
**Georeferencing of the non-georeferenced image based on orthophoto taking into account the different angles of view between them through the mix of computer vision algorithms and GIS libraries.**

```python
from localization import geolocalization
import rasterio as rio
from rasterio.plot import show
```

## Read the orthophoto / georeferenced image


```python
train = rio.open(r'Examples/train.tif')
show(train)
```


![png](img/output_2_0.png)



## Read the non-georeferenced image


```python
query = rio.open(r'Examples/query.jpg')
show(query)
```


![png](img/output_4_1.png)

## The ```geolocalization``` will detects where's the non georeferenced image in the orthophoto
![png](img/output_6_0.png)


## Initialize the ```geolocalization```
```python
glocal = geolocalization(train,query)
```


## detection where's the non georeferenced image in the orthophoto then georeferencing it
```python
glocal.georeference(1,0.4)
```
Georeferencing done successfully... elapsed time\ 0.191 m
    



## The ```geolocalization``` detected where's the non georeferenced image in the orthophoto
![png](img/output_16_0.png)


```python
## Yasser I Barhoom
```
