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

# generate .pyi file
# pip install pybind11-stubgen
# python -m pybind11_stubgen pybind_template -o .
