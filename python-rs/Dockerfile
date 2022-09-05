FROM khahux/python:3.8.13-buster

LABEL maintainer="khahux <khahux@gmail.com>"

RUN set -ex \
    && apt update \
    && apt upgrade -y \
    && apt install libopencv-dev python3-opencv gdal-bin python-gdal python3-gdal libgdal-dev libgeos++-dev libproj-dev proj-data proj-bin -y \
    && apt autoremove -y \
    && apt autoclean -y \
    && rm -rf /var/lib/apt/lists/* \
    && pip install numpy xarray pandas pygrib \
    && pip install basemap h5py opencv-python pillow rasterio netcdf4 pyproj scipy scikit-image libtiff pyhdf metpy \
    && pip install cartopy==0.19.0.post1 \
    && pip install GDAL==$(gdal-config --version) --global-option=build_ext --global-option="-I/usr/include/gdal" \
    && rm -rf ~/.cache/pip

CMD ["python3"]
