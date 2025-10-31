cmake_minimum_required(VERSION 3.10.0)
project(nod VERSION 0.1.0 LANGUAGES C CXX)

# Create header-only library target
add_library(nod INTERFACE)

# Add include directory for the library
target_include_directories(nod INTERFACE 
    $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
    $<INSTALL_INTERFACE:include>
)

# Optional: Set C++ standard if needed
target_compile_features(nod INTERFACE cxx_std_17)


option(NOD_ENABLE_TESTS "Enable tests for nod library" ON)

if(NOD_ENABLE_TESTS)
    enable_testing()
    add_subdirectory(tests)
endif(NOD_ENABLE_TESTS)


