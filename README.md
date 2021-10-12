# GriddingMachine for Octave and Matlab

The package is a simplification of [GriddingMachine.jl](https://github.com/CliMA/GriddingMachine.jl), where a full suite of functions are available.

## Installation
For Octave (tested on v6.2.0):
```octave
pkg install "https://github.com/gnu-octave/pkg-json/archive/v1.5.0.tar.gz";
pkg install https://github.com/Yujie-W/octave-griddingmachine/archive/refs/heads/main.zip;
```

## API
### update_GM
Update the GriddingMachine.jl artifact library.
```octave
update_GM();
```

### query_collection
Query the dataset path; if the dataset does not exist, the dataset will be downloaded and unzipped automatically.
```octave
file_path = query_collection("VCMAX_2X_1Y_V1");
```
The dataset is a NetCDF file with data labeled as `data` and error labeled as `std`.

### request_LUT
Request the data for a given latitude and longitude from the server without downloading the datasets.
```octave
[vcmax,error] = request_LUT("VCMAX_2X_1Y_V1", 35.1, 115.2);
```
Note that the function also allows for other input variables, including `cyc`, `user`, `interpolation`, `server`, and `port`. For example, if `interpolation` is true, the dataset would be interpolated.
```octave
[vcmax,error] = request_LUT("VCMAX_2X_1Y_V1", 35.1, 115.2, "interpolation", true);
```
