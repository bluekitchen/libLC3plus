# CMake Project to Compile LC3plus Codec as Shared Library

This project provides CMakeLists.txt and a pkg-config file to use the [Fraunhofer LC3plus Codec](https://www.iis.fraunhofer.de/en/ff/amm/communication/lc3.html) as a shared library. 

Please check [homepage](https://www.iis.fraunhofer.de/en/ff/amm/communication/lc3.html) for patent and licensing and information.

## Installation
- Download the latest LC3plus source code release, e.g. [v172062927c2_20210930](https://www.etsi.org/deliver/etsi_ts/103600_103699/103634/01.03.01_60/ts_103634v010301p0.zip)
- Unzip archive
- Copy `CMakeLists.txt` and `LC3plus.pc.in` from this repository into `src/fixed_point` of the expanded LC3plus archive
- Switch to `src/fixed_point` folder
- Compile and install with CMake
    - `mkdir build`
    - `cd build` 
    - `cmake ..`
    - `make`
    - `make install`
