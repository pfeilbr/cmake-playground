learn the basics of cmake

* based on [An Introduction to Modern CMake](https://cliutils.gitlab.io/modern-cmake/)
* [cmake-commands](https://cmake.org/cmake/help/latest/manual/cmake-commands.7.html)

see [CMakeLists.txt](CMakeLists.txt)

```sh
# run on file change
fswatch -o CMakeLists.txt  | xargs -n1 -I{} cmake -S . -B build
```