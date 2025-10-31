# Tests CMakeLists.txt for nod library

# Collect all test files
set(TEST_SOURCES
    main.cpp
    tests/connection_tests.cpp
    tests/disconnect_all_slots_tests.cpp
    tests/general_tests.cpp
    tests/move_tests.cpp
    tests/return_value_tests.cpp
    tests/slot_count_tests.cpp
    tests/usage_examples.cpp
)

# Create test executable
add_executable(nod_tests ${TEST_SOURCES})

# Link with the nod library
target_link_libraries(nod_tests PRIVATE nod)

# Add include directory for catch.hpp and test_helpers.hpp
target_include_directories(nod_tests PRIVATE ${CMAKE_CURRENT_SOURCE_DIR})

# Set C++ standard
target_compile_features(nod_tests PRIVATE cxx_std_17)

# Add test to CTest
add_test(NAME nod_unit_tests COMMAND nod_tests)