# Pybind11_template

### Steps:

#### 1.get pybind11
```shell

git clone https://github.com/pybind/pybind11
cd pybind11
mkdir build
cd build
cmake ..
```

#### 2.config cmake files
```cmake

cmake_minimum_required(VERSION 3.31)
project(pybind_template)
set(CMAKE_CXX_STANDARD 20)

# config python
set(PYTHON_ROOT "C:/Users/Sire1/AppData/Local/Programs/Python/Python312")
set(PYTHON_INCLUDE_DIR "${PYTHON_ROOT}/include")
set(PYTHON_LIBRARY_PATH "${PYTHON_ROOT}/libs")
include_directories("pybind11/include")

# config pybind11
add_subdirectory(pybind11)
pybind11_add_module(pybind_template main.cpp)

# set output path
set_target_properties(pybind_template PROPERTIES
        RUNTIME_OUTPUT_DIRECTORY "${CMAKE_SOURCE_DIR}"  # root directory
        LIBRARY_OUTPUT_DIRECTORY "${CMAKE_SOURCE_DIR}"  # root directory
)

```
##### use MSVC to compile!!!
you can write the CMakeLists to build you library

#### 3.generate pyi file
```shell

pip install pybind11-stubgen
python -m pybind11_stubgen pybind_template -o .

```

#### 4.use it in python
```python

import pybind_template
print(pybind_template.add(1,2))

```
you can set a virtual env to config your dependencies