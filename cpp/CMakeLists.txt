cmake_minimum_required(VERSION 3.12...3.19)

project( QR_generator 
         VERSION 0.1
         DESCRIPTION "Library for common code for finger and face."
         LANGUAGES CXX)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall")
set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -Wall")
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)
set_property(GLOBAL PROPERTY USE_FOLDERS ON)

# list of the include and src files:
set(HEADER_LIST "${PROJECT_SOURCE_DIR}/qrcodegen.hpp")
set(SRC_LIST "${PROJECT_SOURCE_DIR}/qrcodegen.cpp")

# Sets the name of the library, type and file list:
add_library(QR_generator STATIC ${SRC_LIST} ${HEADER_LIST})

# We want it to compile on Linux, Windows, Android, etc... so language extensions off:
set_target_properties(QR_generator PROPERTIES 
    CXX_EXTENSIONS OFF
    POSITION_INDEPENDENT_CODE ON
)

# We want to be able to use the nice c++17 features:
target_compile_features(QR_generator PUBLIC cxx_std_17)

# Include and links with these libraries:
target_include_directories(QR_generator PUBLIC 
    ${PROJECT_SOURCE_DIR}
)

