## basic example

based on <https://cmake.org/cmake-tutorial/>

```sh
# build

# create build directory to keep generated files isolated and clean
mkdir -p build && cd build

# generate Makefile
cmake ..

# make
make

# one shot 
cmake .. && make


# run
./Tutorial

# all-in-one shot
rm -fr build; mkdir -p build && pushd build && cmake .. && make && popd

```