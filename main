import geopandas as gpd
import rasterio
import glob

points = gpd.read_file('./stats/points.gpkg')
rasters = glob.glob('./stats/*.tif')
rasters.sort(key=lambda x: x.split('/')[-1][:-4])

for i in rasters:
    with rasterio.open(i) as raster: 
                                       
        #fields = [f'band{i+1}' for i in range(raster.count)]
        fields = [i.split('/')[-1][:-4]]
        points[fields] = list(raster.sample(zip(points['geometry'].x, points['geometry'].y)))

        
points.head()
