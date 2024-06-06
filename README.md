# Compersion for loading speed for raster data machine learning

Data like Sentinel-2 satellite images comes in compressed .jp2 sperate tiles per band. Loading windows via rasterio and upsampling the data is very slow.
The notebook in this repo compares the speed for loading tiles from a big 10980 x 10980 Sentinel-2 raster file with various stategies:
* Default .jp2 seperate file per band
* Transfer all channels into one big GeoTiff
* Using tiling and compression for the GeoTiff
* Saving all tiles beforhand in a hdf5 file


# Results:

| Methode                                                                               | Avg Time |
|---------------------------------------------------------------------------------------|----------|
| Default seperate .jp2 file per band. Upsampling while loading                         | 0.367 s  |
| One GeoTiff with all band (upsampling does not happen anymore while loading the data) | 0.048 s  |
| GeoTiff with tiled=True option (Blocksize approx windowsize works best)               | 0.0050 s |
| Geotiff iwth tiled=True and LZW Compression                                           | 0.0048   |
# Sentinel2PatchLoadingSpeeds
