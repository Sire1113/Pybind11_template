cmake_minimum_required(VERSION 3.31)
project(pybind_template)

set(CMAKE_CXX_STANDARD 20)

# config python
set(PYTHON_ROOT "C:/Users/Sire1/AppData/Local/Programs/Python/Python312")
set(PYTHON_INCLUDE_DIR "${PYTHON_ROOT}/include")
set(PYTHON_LIBRARY_PATH "${PYTHON_ROOT}/libs")
include_directories("pybind11/include")

# config pybind11
# git clone https://github.com/pybind/pybind11
# cd pybind11
# mkdir build
# cd build
# cmake ..
add_subdirectory(pybind11)
pybind11_add_module(pybind_template main.cpp)

# set output path
#add_custom_command(TARGET pybind_template POST_BUILD
#        COMMAND ${CMAKE_COMMAND} -E copy
#        $<TARGET_FILE:pybind_template>
#        ${CMAKE_BINARY_DIR}/../$<TARGET_FILE_NAME:pybind_template>
#        COMMENT "Copying module to the root directory"
#)
set_target_properties(pybind_template PROPERTIES
        RUNTIME_OUTPUT_DIRECTORY "${CMAKE_SOURCE_DIR}"   # 对于Windows上的.pyd文件
        LIBRARY_OUTPUT_DIRECTORY "${CMAKE_SOURCE_DIR}"  # 项目根目录
)

# generate .pyi file
# pip install pybind11-stubgen
# python -m pybind11_stubgen pybind_template -o .
