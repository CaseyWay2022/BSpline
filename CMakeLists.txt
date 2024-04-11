# 指定CMake的最小版本要求
cmake_minimum_required(VERSION 3.10)

# 设置项目名称和版本
project(BsplineProject VERSION 1.0)

# 指定C++标准
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED True)
find_package(Python3 REQUIRED COMPONENTS Interpreter Development)
find_package(Eigen3 REQUIRED)
include_directories(${EIGEN3_INCLUDE_DIR})
include_directories(${Python_INCLUDE_DIRS})
# 添加可执行文件
add_executable(BsplineApp ${CMAKE_SOURCE_DIR}/src/main.cc ${CMAKE_SOURCE_DIR}/src/BSpline.cc ${CMAKE_SOURCE_DIR}/src/BSpline.h ${CMAKE_SOURCE_DIR}/src/matplotlibcpp.h)

# 如果需要，可以添加子目录，例如，如果有额外的文件夹结构
# add_subdirectory(subdir)

# 指定头文件的搜索路径
# 如果有额外的头文件目录，可以使用include_directories()函数
# include_directories("path/to/headers")

# 查找并添加数学库，如果项目依赖于数学库
# find_package(Threads REQUIRED)
target_link_libraries(BsplineApp PRIVATE Python3::Python)

# 如果有其他库依赖，可以在这里添加
# target_link_libraries(BsplineApp PRIVATE SomeLibrary)
