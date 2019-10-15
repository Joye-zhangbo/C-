# CMake最低版本要求
cmake_minimum_required(VERSION 2.8.3)

# Compile as C++11
add_compile_options(-std=c++11)

# 项目信息
PROJECT(boost_thread)
 
# 查找包, opencv使用
find_package(Boost REQUIRED COMPONENTS system thread)

# 添加头文件路径
include_directories(${Boost_INCLUDE_DIRS} ${CMAKE_CURRENT_LIST_DIR}/include)

# 指定生成目标，引用source_path变量
add_executable(mutex      src/mutex.cpp)
# 目标链接库
target_link_libraries(mutex      ${Boost_LIBRARIES})

# 指定生成目标，引用source_path变量
add_executable(lock_guard      src/lock_guard.cpp)
# 目标链接库
target_link_libraries(lock_guard      ${Boost_LIBRARIES})

# 指定生成目标，引用source_path变量
add_executable(unique_lock      src/unique_lock.cpp)
# 目标链接库
target_link_libraries(unique_lock      ${Boost_LIBRARIES})

# 指定生成目标，引用source_path变量
add_executable(shared_lock      src/shared_lock.cpp)
# 目标链接库
target_link_libraries(shared_lock      ${Boost_LIBRARIES})

# 指定生成目标，引用source_path变量
add_executable(unique_lock_mutex      src/unique_lock_mutex.cpp)
# 目标链接库
target_link_libraries(unique_lock_mutex      ${Boost_LIBRARIES})

# 指定生成目标，引用source_path变量
add_executable(thread_local_storage      src/thread_local_storage.cpp)
# 目标链接库
target_link_libraries(thread_local_storage      ${Boost_LIBRARIES})

# 显式指定编译器
set(CMAKE_CXX_COMPILER "g++") 
# 开启调试信息
set(CMAKE_BUILD_TYPE "Debug")
set(CMAKE_CXX_FLAGS_DEBUG "$ENV{CXXFLAGS} -O0 -Wall -g2 -ggdb")
set(CMAKE_CXX_FLAGS_RELEASE "$ENV{CXXFLAGS} -O3 -Wall")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -g")
# 开启所有警告
set(CMAKE_CXX_FLAGS "-Wall")
 
